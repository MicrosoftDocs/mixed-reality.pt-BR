---
title: Módulo básico de aprendizado de MR – entrada avançada
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 32141aafd43c5d729919673509c93bb2014edd37
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719889"
---
# <a name="mr-learning-base-module---advanced-input"></a>Módulo básico de aprendizado de MR – entrada avançada

Nesta lição, exploraremos várias opções avançadas de entrada para o HoloLens 2, incluindo o uso de comandos de voz, o gesto de panorâmica e o acompanhamento ocular. 

## <a name="objectives"></a>Objetivos

- Aprender a disparar eventos usando palavras-chave e comandos de voz
- Usar mãos rastreadas para aplicar a panorâmica de texturas e objetos 3D
- Aproveitar funcionalidades de acompanhamento ocular do HoloLens 2 para selecionar objetos

## <a name="instructions"></a>Instruções

### <a name="enabling-voice-commands"></a>Habilitando comandos de voz

Nesta seção, implementaremos dois comandos de voz. Primeiro, a capacidade de alternar o painel de diagnóstico de taxa de quadros dizendo "ativar/desativar diagnóstico". Segundo, a capacidade de reproduzir um som com um comando de voz. Primeiro, exploraremos os perfis do MRTK e as configurações responsáveis por definir comandos de voz. 

1. Na hierarquia da cena base, selecione "MixedRealityToolkit". No painel do inspetor, role para baixo até as configurações do sistema de entrada. Clique duas vezes para abrir o perfil de sistema de entrada. Clone o perfil de sistema de entrada para torná-lo editável, como já vimos na [Lição 1](mrlearning-base-ch1.md) 

O perfil de sistema de entrada, você verá uma variedade de configurações. Para comandos de voz, desça até a opção que diz "Configurações do Comando de Fala". 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. Clone o perfil de comandos de fala para torná-lo editável, como já vimos na [Lição 1](mrlearning-base-ch1.md). Clique duas vezes no perfil de comando de fala, em que você perceberá uma variedade de configurações. Para obter uma descrição completa dessas configurações, consulte a [documentação de fala do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Observação: Por padrão, o comportamento geral é iniciado automaticamente. Isso pode ser alterado para a iniciação manual se desejado, mas, para este exemplo, vamos mantê-lo no início automático. O MRTK vem com vários comandos de voz padrão (por exemplo, menu ativar/desativar diagnóstico e ativar/desativar criador de perfil). Usaremos a palavra-chave "ativar/desativar diagnóstico" para ativar e desativar o contador da taxa de quadros de diagnóstico. Também adicionaremos um novo comando de voz nas etapas abaixo.
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. Adicione um novo comando de voz. Para adicionar um novo comando de voz, clique no botão "+ adicionar um novo comando de fala" e você verá uma nova linha que aparece abaixo da lista dos comandos de voz existentes. Digite o comando de voz que você deseja usar. Neste exemplo, usaremos o comando “reproduzir música”.

>Dica: Você também pode definir um keycode para comandos de fala. Isso permite que os comandos de voz sejam disparados após pressionar uma tecla no teclado.   

4. Adicione a capacidade de responder a comandos de voz. Selecione qualquer objeto na hierarquia da cena base que não tenha nenhum outro script de entrada anexado a ele (por exemplo, nenhum manipulador de manipulação). No painel do inspetor, clique em "adicionar componente". Digite "manipulador de entrada de fala". Selecione-o.
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

Por padrão, você verá 2 caixas de seleção, uma é a caixa de seleção "é o foco necessário". Isso significa que enquanto você estiver apontando para o objeto com um raio de foco, (foco do olhar, foco com a cabeça, foco do controlador, foco com a mão) o comando de voz será disparado. Desmarque essa caixa de seleção para que o usuário não precise olhar para o objeto para usar o comando de voz.

5. Adicione a capacidade de responder a um comando de voz. Para fazer isso, clique no botão "+" que está no manipulador de entrada de fala e selecione a palavra-chave à qual você gostaria de responder.

   > Observação: Essas palavras-chave são preenchidas com base no perfil editado na etapa anterior.

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. Ao lado de "Palavra-chave", você verá um menu suspenso. Selecione "Ativar/desativar diagnóstico". Isso fará com que sempre que o usuário disser a frase "ativar/desativar diagnóstico", uma ação será disparada. Observe que você talvez precise expandir "elemento 0" ao pressionar a seta ao lado dele.

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. Adicione o "script de controle de demonstração do diagnóstico" para ativar/desativar o diagnóstico de contador da taxa de quadros. Para fazer isso, pressione o botão "adicionar componente" e pesquise "script de controle de demonstração do diagnóstico", em seguida, adicione-o do menu. Esse script pode ser adicionado a qualquer objeto, mas para simplificar, nós o adicionaremos ao mesmo objeto como o manipulador de entrada de fala. 

   > Observação: esse script é apenas incluído nesses módulos e não está incluído no MRTK original.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. Adicione uma nova resposta no Manipulador de Entrada de Fala. Para fazer isso, clique no botão "+" abaixo do local em que está escrito "resposta ()" (marcado por uma seta verde na figura acima).

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. Arraste o objeto que tem o script de Controles de Demonstração do Diagnóstico para a nova resposta que você criou na etapa 8.
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. Agora selecione a lista suspensa "nenhuma função", selecione os controles de demonstração do diagnóstico e "em ativar/desativar diagnóstico ()". Essa função ativa e desativa o diagnóstico.  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> Observe que antes de compilar para seu dispositivo você precisa habilitar as configurações do microfone. Para fazer disso, clique em arquivo, vá para as configurações de build e, a daí, configurações do player e verifique se a funcionalidade de microfone está configurada.

Em seguida, estamos adicionando a capacidade de reproduzir um arquivo de áudio do comando de voz usando o objeto "octa". Lembre-se da [lição 4](mrlearning-base-ch4.md), adicionamos a capacidade de reproduzir um clipe de áudio tocando o objeto octa. Aproveitaremos essa mesma fonte de áudio para nosso comando de voz de música.

11. Selecione o objeto "octa" na hierarquia da cena base.

12. Adicione outro manipulador de entrada de fala (repita as etapas 4 e 5), mas com o objeto octa. 

13. Em vez de adicionar o comando de voz "Ativar/desativar diagnóstico" da etapa 6, adicione o comando de voz "reproduzir música", conforme mostrado na imagem abaixo.
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Assim como com as etapas 8 e 9, adicione uma nova resposta e arraste o octa para o slot vazio na resposta.

15. Selecione o menu suspenso que diz "nenhuma função," selecione "Fonte de Áudio", em seguida, selecione "PlayOneShot (AudioClip)".

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. Para o clipe de áudio para este exemplo, usaremos o mesmo clipe de áudio da [Lição 4](mrlearning-base-ch4.md). Entre no seu painel do projeto, pesquise o clipe de áudio "MRTK_Gem" e arraste-o para o slot de fonte de áudio, conforme mostrado na imagem abaixo. Agora, seu aplicativo deve ser capaz de responder aos comandos de voz "ativar/desativar diagnóstico" para ativar/desativar o painel de contador da taxa de quadros e "reproduzir música" para reproduzir a música MRTK_Gem.
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>O gesto de panorâmica 

Neste capítulo, aprenderemos a usar o gesto de panorâmica. É útil para rolagem (usando seu dedo ou mão para rolar pelo conteúdo). Você também pode usar o gesto de panorâmica para girar objetos, para percorrer uma coleção de objetos 3D ou até mesmo rolar uma interface do usuário 2D. Aprenderemos como usar o gesto de panorâmica para distorcer uma textura. Também exploraremos como mover uma coleção de objetos 3D.

1. Crie um quadrante. Em sua hierarquia da cena base, clique com o botão direito do mouse, selecione "Objeto 3D" e selecione "Quadrante".

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. Reposicione o quadrante conforme apropriado. Para nosso exemplo, definimos o x = 0, o y = 0 e o z = 1,5 de distância da câmera para uma posição confortável de HoloLens 2.

   > Observação: Se o quadrante bloquear (estiver na frente de) qualquer conteúdo das lições anteriores, certifique-se de movê-lo, de modo que não bloqueie nenhum dos outros objetos.

3. Aplique um material ao quadrante. Este material será o material pelo qual rolaremos com o gesto de panorâmica. 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. No seu painel de projetos, digite na caixa de pesquisa "conteúdo de panorâmica". Arraste esse material para o quadrante na sua cena. 

> Observação: O material de "Aplicar panorâmica de conteúdo" não está incluído no MRTK, mas é um ativo no pacote de ativos deste módulo, conforme importados nas lições anteriores. 

> Observação: Quando você adiciona o conteúdo de panorâmica, ele pode ser ampliado. Você pode corrigir isso ajustando os valores de x, y e z do tamanho do quadrante até estar satisfeito com aparência dele.

Para usar o gesto de panorâmica, será necessário um colisor em seu objeto. Você pode ver que o quadrante já tem um colisor de malha. No entanto, o colisor de malha não é ideal, porque ele é extremamente fino e difícil de selecionar. Sugerimos que você substitua o colisor de malha por um colisor de caixa.

5. Clique com o botão direito do mouse no colisor de malha que está no quadrante (no painel do inspetor) e em seguida, remova-o clicando em "remover componente". 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. Agora, adicione o colisor de caixa clicando em "adicionar componente" e pesquisando por "colisor de caixa". O colisor de caixa padrão adicionado ainda é muito fino, então, clique no botão "editar colisor" para editá-lo. Quando ele é pressionado, você pode ajustar o tamanho usando os valores de x, y e z ou os elementos no editor de cena. Para nosso exemplo, gostaríamos de estender o colisor caixa um pouco atrás do quadrante. No editor de cena, arraste o colisor de caixa da parte de trás, para as extremidades (veja a imagem abaixo). Isso permitirá que o usuário não apenas use o dedo, mas toda a mão para rolar. 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. Torne interativo. Como queremos interagir diretamente com o quadrante, queremos usar o componente "tocável de interação próxima" (também usamos isso na Lição 4 para reproduzir música do octa). Clique em "adicionar componente" e pesquise "tocável de interação próxima" e selecione-o, conforme mostrado nas imagens a seguir. 

8. Adicione a capacidade de reconhecer o gesto de panorâmica. Clique em "adicionar componente" e digite "panorâmica de interação com a mão". Você terá uma opção entre raio de mão (permitindo que você aplique a panorâmica à distância) e o dedo indicador. Neste exemplo, deixe a opção de dedo indicador. 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. No script de panorâmica de interação com a mão, as caixas de seleção “bloqueio horizontal” e “bloqueio vertical” bloquearão os movimentos, respectivamente. As configurações de quebra de textura farão com que a textura (mapeamento da textura) siga os movimentos de panorâmica do usuário. Para este exemplo, marcaremos essa caixa. Também há a “velocidade ativa” que, se for deixada desmarcada, o gesto de panorâmica não funcionará. Marque essa caixa também. Agora você deve ter um quadrante com panorâmica habilitada.

   

   Em seguida, aprenderemos como aplicar panorâmica a objetos 3D. 

10. Clique com o botão direito do mouse no objeto do quadrante, selecione o objeto 3D e clique em "cubo". Dimensione o cubo para que ele tenha aproximadamente x = 0,1, y = 0,1 e z = 0,1. Copie esse cubo 3 vezes (clicando com o botão direito do mouse no cubo e pressionando a opção duplicar ou pressionando o controle/comando D). Espace-os uniformemente. Sua cena deve ser semelhante à imagem abaixo.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. Selecione o quadrante novamente e, sob o script de panorâmica de interação com a mão, queremos definir as ações de panorâmica para cada um dos cubos. Em "receptores de evento de panorâmica", queremos especificar o número de objetos que estão recebendo o evento. Como há 4 cubos, digite "4" e pressione Enter. Devem aparecer 4 campos vazios.


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. Arraste cada um dos cubos para cada um dos slots de elemento vazio.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Adicione o script de "mover com a panorâmica" para todos os cubos. Para fazer isso, pressione e mantenha pressionado o controle/comando e selecione cada objeto. Em seguida, no painel do inspetor, clique em “adicionar componente” e pesquise “mover com a panorâmica”. Clique no script e ele será adicionado a cada cubo. Agora, os objetos 3D serão movidos com o gesto de panorâmica. Se você remover a renderização da malha no seu quadrante, terá um quadrante invisível em que poderá aplicar a panorâmica por uma lista de objetos 3D.

### <a name="eye-tracking"></a>Acompanhamento Ocular

Neste capítulo, exploraremos como habilitar o acompanhamento ocular em nossa demonstração. Giraremos lentamente nossos itens de menu 3D quando eles estiverem sendo focados com os olhos. Também dispararemos um efeito divertido quando o item focado for selecionado.

1. Certifique-se de que os perfis do Kit de Ferramentas de Realidade Misturada estejam configurados corretamente. No momento da redação deste artigo, a configuração de perfil do Kit de Ferramentas de Realidade Misturada não inclui funcionalidades de acompanhamento ocular por padrão. Para adicionar funcionalidades de acompanhamento ocular, siga as instruções na seção “Configurando os perfis do MRTK necessários para o acompanhamento ocular” conforme descrito na [Documentação do Kit de Ferramentas de Realidade Misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ). Certifique-se de que o acompanhamento ocular esteja configurado adequadamente seguindo todas as etapas restantes no link da documentação acima, incluindo habilitar o acompanhamento ocular no GazeProvider (componente anexado à câmera) e habilitar a simulação do acompanhamento ocular no editor do Unity. Observe que a versão futura do MRTK pode incluir o acompanhamento ocular por padrão.

    O link acima fornece breves instruções para:

    - Criar o Provedor de Dados de Foco do Olhar para uso no perfil do MRTK
    - Habilitar o acompanhamento ocular do Provedor de Foco
    - Configurar para a simulação do acompanhamento ocular no editor
    - Editar as funcionalidades da solução do Visual Studio para permitir o acompanhamento ocular no aplicativo criado

2. Adicione o componente de Destino de Acompanhamento Ocular aos objetos de destino. Para permitir que um objeto responda a eventos de foco do olhar, precisaremos adicionar o componente EyeTrackingTarget em cada objeto com os quais desejamos interagir usando o foco do olhar. Adicione esse componente a cada um dos nove objetos 3D que fazem parte da coleção de grade. Dica: selecione vários itens na hierarquia para adicionar em massa o componente EyeTrackingTarget.
    ![Lesson5 Chapter3 Step2](images/Lesson5Chapter3Step2.JPG)

3. Em seguida, adicionaremos o script EyeTrackingTutorialDemo para algumas interações interessantes. O script EyeTrackingTutorialDemo é incluído como parte do repositório desta série de tutoriais e não está incluído por padrão com o Kit de Ferramentas de Realidade Misturada. Para cada objeto 3D na coleção de grade, adicione o script de EyeTrackingTutorialDemo pesquisando pelo componente no menu "Adicionar Componente".
   ![Lesson5 Chapter3 Step3](images/Lesson5Chapter3Step3.JPG)

   4. Gire o objeto enquanto olha para o destino. Gostaríamos de configurar o nosso objeto 3D para girar enquanto estamos olhando para ele. Para fazer isso, insira um novo campo na seção "Enquanto Estiver Olhando para o Destino" do componente EyeTrackingTarget, conforme mostrado na imagem abaixo. 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



No campo recém-criado, adicione o objeto do jogo atual ao campo vazio e selecione EyeTrackingTutorialDemo > RotateTarget() conforme mostrado na imagem abaixo. Agora o objeto 3D está configurado para girar quando estiver sendo focado com o acompanhamento ocular. 

5. Adicione a capacidade de “emitir um breve sinal sonoro para o destino” que está sendo focado ao ser selecionado (fechar e abrir dedos indicador e polegar ou dizendo “selecionar”). Semelhante à etapa 4, queremos disparar EyeTrackingTutorialDemo > BlipTarget() atribuindo-o ao campo “Select()” do objeto do jogo do componente EyeTrackingTarget, conforme mostrado na figura abaixo. Com esse recurso configurado agora, você notará um breve sinal sonoro no objeto do jogo sempre que você disparar uma ação de seleção, como fechar e abrir os dedos indicador e polegar ou usar o comando de voz “selecionar”. 
    ![Lesson5 Chapter3 Step5](images/Lesson5Chapter3Step5.JPG)
6. Certifique-se de que as funcionalidades de acompanhamento ocular estejam configuradas adequadamente antes de compilar para o HoloLens 2. No momento da redação deste artigo, a Unity ainda não tem a capacidade de definir a funcionalidade de entrada de foco (para o acompanhamento ocular). A configuração dessa funcionalidade é necessária para o acompanhamento ocular funcionar no HoloLens 2. Siga estas instruções na documentação do Kit de Ferramentas de Realidade Misturada para habilitar a funcionalidade de entrada de foco: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>Parabéns! 
Você adicionou com êxito as funcionalidades de acompanhamento ocular ao aplicativo. Essas ações são apenas o começo de um mundo de possibilidades com o acompanhamento ocular. Este capítulo também conclui a lição 5, em que aprendemos sobre funcionalidades de entrada avançadas, como comandos de voz, gestos de movimento panorâmico e acompanhamento ocular. 

[Próxima lição: Experiência de exemplo do assembly de módulo Lunar](mrlearning-base-ch6.md)

