---
title: Tutoriais de introdução-6. Explorando opções de entrada avançadas
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: b740c463e3d73d5df9b996562e9ff0a1952703f0
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064314"
---
# <a name="6-exploring-advanced-input-options"></a>6. explorando opções de entrada avançadas

Neste tutorial, várias opções de entrada avançadas para o HoloLens 2 são exploradas, incluindo o uso de comandos de voz, gesto de panorâmica e acompanhamento de olho. 

## <a name="objectives"></a>Objetivos

- Disparar eventos usando comandos de voz e palavras-chave
- Usar mãos controladas para deslocar texturas e objetos 3D com mãos controladas
- Aproveitar os recursos de acompanhamento de olho do HoloLens 2 para selecionar objetos

## <a name="instructions"></a>Instruções

### <a name="enabling-voice-commands"></a>Habilitando comandos de voz

Nesta seção, dois comandos de voz são implementados. Primeiro, a capacidade de alternar o painel de diagnóstico de taxa de quadros é introduzida dizendo "Toggle Diagnostics". Em segundo lugar, a capacidade de tocar um som com um comando de voz é explorada. Os perfis e as configurações do MRTK responsáveis pela configuração de comandos de voz são examinados primeiro.

1. Na hierarquia BaseScene, selecione MixedRealityToolkit. Em seguida, no painel Inspetor, selecione entrada e clique no botão clone pequeno à esquerda do DefaultMixedRealityInputSystemProfile para abrir o pop-up perfil de clonagem. Na janela pop-up, clique em clonar para criar um novo perfil MixedRealityInputSystemProfile.

    ![mrlearning-base-CH5-1-step1a. png](images/mrlearning-base-ch5-1-step1a.png)

    Isso também preencherá automaticamente o MixedRealityToolkitConfigurationProfile com a MixedRealityInputSystemProfile recém-criada.

    ![mrlearning-base-CH5-1-step1b. png](images/mrlearning-base-ch5-1-step1b.png)

2. No perfil do sistema de entrada, há uma variedade de configurações. Para comandos de voz, expanda a seção fala e siga o mesmo processo da etapa anterior para clonar o DefaultMixedRealitySpeechCommandsProfile e substituí-lo por sua própria cópia editável.

    ![mrlearning-base-CH5-1-Step2. png](images/mrlearning-base-ch5-1-step2.png)

    No perfil de comando de fala, você observará uma variedade de configurações. Para obter uma descrição completa dessas configurações, consulte a [documentação de fala do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>).

    Por padrão, o comportamento geral é iniciado automaticamente. Isso pode ser alterado para início manual, se desejado. Mas, para este exemplo, mantenha-o em início automático. O MRTK vem com vários comandos de voz padrão, como menu, alternância de diagnóstico e alternância do profiler. Usaremos a palavra-chave "Toggle Diagnostics" para ativar e desativar o contador diagnóstico taxa de quadros. Também adicionaremos um novo comando de voz nas etapas abaixo.

3. Adicione um novo comando de voz. Para fazer isso, clique no botão + Adicionar um novo comando de fala. Você verá uma nova linha que aparece abaixo da lista de comandos de voz existentes. Digite o comando de voz que você deseja usar. Neste exemplo, use o comando "reproduzir música".

    ![mrlearning-base-CH5-1-Step3. png](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    >Você também pode definir um keycode para comandos de fala. Isso permite que os comandos de voz disparem eventos após a prensa de uma tecla de teclado.

4. Adicione a capacidade de responder a comandos de voz. Selecione qualquer objeto na hierarquia BaseScene que não tenha outros scripts de entrada anexados a ele, por exemplo, o objeto de jogo MixedRealityPlayspace. No painel Inspetor, clique em Adicionar componente, pesquise por "fala" e selecione o script do manipulador de entrada de fala.

    ![mrlearning-base-CH5-1-step4. png](images/mrlearning-base-ch5-1-step4.png)

    Por padrão, você verá duas caixas de seleção. Uma é a caixa de seleção é o foco necessário. Portanto, desde que você esteja apontando para o objeto com um raio de olhar, olhar, Controller-olhar ou Hand-olhar, o comando de voz será disparado. Desmarque essa caixa de seleção para que o usuário não precise examinar o objeto para usar o comando de voz.

5. Adicione a capacidade de responder a um comando de voz. Para fazer isso, clique no botão + que está no manipulador de entrada de fala.

    ![mrlearning-base-CH5-1-Step5. png](images/mrlearning-base-ch5-1-step5.png)

6. Ao lado de palavra-chave, você verá um menu suspenso. Selecione Ativar/desativar diagnóstico para que sempre que o usuário disser a frase "ativar/desativar diagnóstico", ele disparará uma ação. Observe que talvez seja necessário expandir o elemento 0 pressionando a seta ao lado dele.

    ![mrlearning-base-CH5-1-step6. png](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    >Essas palavras-chave são preenchidas com base no perfil que você editou na etapa 3.

7. Adicione o script de controles de voz do sistema de diagnóstico para ativar e desativar o diagnóstico do contador de taxa de quadros. Para fazer isso, pressione Adicionar componente, pesquise o diagnóstico sistema voz controles script e adicione-o no menu. Esse script pode ser adicionado a qualquer objeto, mas para simplificar, nós o adicionaremos ao mesmo objeto como o manipulador de entrada de fala.

    ![mrlearning-base-CH5-1-Step7. png](images/mrlearning-base-ch5-1-step7.png)

8. Adicione uma nova resposta no manipulador de entrada de fala. Para fazer isso, clique no ícone "+" para adicionar uma nova resposta à lista de respostas.

    ![mrlearning-base-CH5-1-step8. png](images/mrlearning-base-ch5-1-step8.png)

9. Arraste o objeto que tem o diagnóstico sistema de voz controles script para a nova resposta que você acabou de criar na etapa anterior.

    ![mrlearning-base-CH5-1-Step9. png](images/mrlearning-base-ch5-1-step9.png)

10. Clique na lista suspensa função (onde ela não diz nenhuma função), em seguida, diagnóstico do sistema de voz e selecione a função ToggleDiagnostics () que ativa e desativa o diagnóstico.

    ![mrlearning-base-CH5-1-step10. png](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > Antes de criar seu dispositivo, você precisa habilitar as configurações do MIC. Para fazer isso, clique em arquivo e vá para configurações de compilação, configurações do Player e verifique se a capacidade do microfone está definida.

    Em seguida, adicione a capacidade de reproduzir um arquivo de áudio do comando de voz usando o objeto Octa. Lembre-se da [lição 4](mrlearning-base-ch4.md) que a capacidade de reproduzir um clipe de áudio tocando no objeto Octa foi adicionada. Aproveitaremos essa mesma fonte de áudio para nosso comando de voz de música.

11. Selecione o objeto Octa na hierarquia BaseScene.

12. Adicione outro manipulador de entrada de fala (repita as etapas 4 e 5), mas com o objeto Octa.

13. Em vez de adicionar o comando Ativar voz de diagnóstico da etapa 6, adicione o comando reproduzir música Voice, conforme mostrado na imagem abaixo.

    ![mrlearning-base-CH5-1-step13. png](images/mrlearning-base-ch5-1-step13.png)

14. Assim como nas etapas 8 e 9, adicione uma nova resposta e arraste o objeto Octa, o objeto que tem o diagnóstico sistema de voz controla o script nele, para o slot de resposta vazio.

15. Selecione o menu suspenso que não diz nenhuma função. Em seguida, selecione fonte de áudio, seguida por PlayOneShot (AudioClip).

    ![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. Para este exemplo, vamos usar o mesmo clipe de áudio da [lição 4](mrlearning-base-ch4.md). Acesse o painel de projeto, pesquise por "MRTK_Gem" clipe de áudio e arraste-o para o slot de fonte de áudio, conforme mostrado na imagem abaixo. Agora, seu aplicativo responderá aos comandos de voz "Toggle Diagnostics" para alternar o painel do contador de taxa de quadros e reproduzir música para reproduzir a MRTK_Gem música.

    ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)

### <a name="the-pan-gesture"></a>O gesto de panorâmica

Nesta seção, você aprenderá a usar o gesto de panorâmica. Isso é útil para rolar usando o dedo ou a mão para rolar pelo conteúdo. Você também pode usar o gesto de panorâmica para girar objetos, percorrer uma coleção de objetos 3D ou até mesmo para rolar uma interface do usuário 2D.

1. Crie um quadrante. Na hierarquia do BaseScene, clique com o botão direito do mouse, selecione "objeto 3D" seguido por Quad.

    ![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. Reposicione o quad, conforme apropriado. Para nosso exemplo, definimos o x = 0, y = 0 e z = 1,5 fora da câmera para uma posição confortável do HoloLens 2.

    >[!NOTE]
    >Se os blocos quádruplos ou estiverem na frente de qualquer conteúdo das lições anteriores, certifique-se de movê-lo para que ele não bloqueie nenhum dos outros objetos.

3. Aplique um material ao quadrante. Esse material será o que iremos rolar com o gesto de panorâmica.

    ![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. No painel projetos, digite "conteúdo panorâmico" na caixa de pesquisa. Arraste esse material para o quad em sua cena.

    >[!NOTE]
    >O material PanContent não faz parte do MRTK, mas está incluído com o ativo BaseModuleAssets importado na lição anterior.

    Para usar o gesto de panorâmica, será necessário um colisor em seu objeto. Você pode ver que o quadrante já tem um colisor de malha. No entanto, o colisor de malha não é ideal, porque ele é extremamente fino e difícil de selecionar. Sugerimos que você substitua o colisor de malha por um colisor de caixa.

5. Clique com o botão direito do mouse no Colisor de malha que está no Quad no painel inspetor. Em seguida, remova-o clicando em remover componente.

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. Agora, adicione o colisor de caixa clicando em Adicionar componente e procurando "Colisor de caixa". O colisor da caixa adicionada padrão ainda é muito fino, portanto, clique no botão Editar colisor para editar. Quando ele é pressionado, você pode ajustar o tamanho usando os valores de x, y e z ou os elementos no editor de cena. Para nosso exemplo, gostaríamos de estender o colisor caixa um pouco atrás do quadrante. No editor de cena, arraste o colisor de caixa da parte de trás, para as extremidades (veja a imagem abaixo). Isso permite que o usuário não use apenas o dedo, mas toda a sua mão para rolar.

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. Torne interativo. Como queremos interagir com o quad diretamente, queremos usar o componente de uso de interação próximo, que usamos isso na lição 4 para reproduzir música do objeto Octa. Clique em Adicionar componente, procure "Near interling touchable" e selecione-o conforme mostrado nas imagens abaixo.

    ![mrlearning-base-CH5-2-step7a. png](images/mrlearning-base-ch5-2-step7a.png)

    Se você vir um aviso amarelo sobre limites e/ou centro que não corresponde ao tamanho e/ou ao centro do BoxCollider, clique nos botões corrigir limites e/ou centro de correção para atualizar os valores de centro e limites.

    ![mrlearning-base-CH5-2-step7b. png](images/mrlearning-base-ch5-2-step7b.png)

8. Adicione a capacidade de reconhecer o gesto de panorâmica. Clique em Adicionar componente, digite "interação à mão" no campo de pesquisa e adicione o componente script de panorâmica de interação de mão.

    ![mrlearning-base-CH5-2-step8a. png](images/mrlearning-base-ch5-2-step8a.png)

    E com isso, você tem um quad habilitado para Pan.

    Como você pode ver, o componente de script do Hand interling panorâmica zoom tem várias configurações, como um exercício opcional, sinta-se à vontade para brincar com elas.

    ![mrlearning-base-CH5-2-step8b. png](images/mrlearning-base-ch5-2-step8b.png)

9. Em seguida, aprenderemos como aplicar panorâmica a objetos 3D.

    Na hierarquia, clique com o botão direito do mouse no objeto Quad, para abrir o menu pop-up contextual e, em seguida, selecione **objeto 3d** > **cubo** para adicionar um cubo à sua cena.

    Verifique se a **posição** do cubo está definida como _0, 0, 0,_ portanto, ela está posicionada de forma organizada no Quad. Dimensione o cubo para uma **escala** de _0,1, 0,1, 0,1_.

    ![mrlearning-base-CH5-2-Step9. png](images/mrlearning-base-ch5-2-step9.png)

    Duplique o cubo três vezes clicando com o botão direito do mouse no cubo para abrir o menu pop-up contextual e selecionando **duplicar**.

    Espaçar os cubos uniformemente. Sua cena deve ser semelhante à imagem abaixo.

10. Adicione o script MoveWithPan a todos os cubos mantendo a tecla CTRL pressionada enquanto seleciona cada objeto de **cubo** no painel hierarquia. No painel Inspetor, clique em Adicionar componente e procure e selecione o script **mover com Pan** para adicioná-lo a todos os cubos.

    ![mrlearning-base-CH5-2-step10a. png](images/mrlearning-base-ch5-2-step10a.png)

    >[!NOTE]
    >O script MoveWithPan não faz parte do MRTK, mas está incluído com o ativo BaseModuleAssets importado na lição anterior.

    Com os cubos ainda selecionados, arraste o objeto **Quad** do painel hierarquia para o campo **fonte de entrada de panorâmica** do componente do script **mover com Pan** .

    ![mrlearning-base-CH5-2-step10b. png](images/mrlearning-base-ch5-2-step10b.png)

    Agora, os cubos serão movidos com o gesto panorâmico.

    >[!TIP]
    >A instância MoveWithPan em cada cubo escuta o evento PanUpdated enviado da instância HandInteractionPanZoom no objeto Quad, que adicionamos ao campo fonte de entrada Pan em cada um dos cubos e atualiza a posição do respectivo objeto de cubo de acordo.

    Com os cubos ainda selecionados, mova-os para frente ao longo de seu eixo Z para que a malha de cada cubo esteja dentro do **colisor da caixa** **quádrupla**, alterando seus valores de **posição Z** para _0,7_.

    ![mrlearning-base-CH5-2-step10c. png](images/mrlearning-base-ch5-2-step10c.png)

    Agora, se você desabilitar o componente de **processador de malha** **quádruplo**, desmarcando-o no painel Inspetor, você terá um quádruplo invisível onde poderá percorrer uma lista de objetos 3D.

    ![mrlearning-base-CH5-2-step10d. png](images/mrlearning-base-ch5-2-step10d.png)

### <a name="eye-tracking"></a>Acompanhamento Ocular

Nesta seção, exploraremos como habilitar o acompanhamento de olho em nossa demonstração. Nós vamos girar lentamente nossos itens de menu 3D quando estiverem sendo gazeddos com o olhar de olho. Também dispararemos um efeito divertido quando o item focado for selecionado.

1. Verifique se os perfis de MRTK estão configurados corretamente para acompanhamento de olho. Para fazer isso, acesse o [Guia de introdução ao acompanhamento de olho em MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instruções e verifique se o acompanhamento de olho está configurado corretamente examinando as etapas na seção Configurando passo a passo de [acompanhamento de olho](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step) . Conclua as etapas restantes na documentação.

    >[!NOTE]
    >Se você usou o DefaultHoloLens2InputSystemProfile, conforme instruído na lição [Configurar o kit de ferramentas da realidade misturada](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit) , para clonar seu perfil de configuração personalizado do MRTK, o acompanhamento de olho é habilitado por padrão no projeto do Unity, mas você ainda precisará configurar a simulação de acompanhamento ocular para o editor do Unity e configurar o Visual Studio para permitir o acompanhamento dos olhos da compilação.

    O link acima fornece breves instruções para:

    - Criando o olhar de olho de realidade mista do Windows Provedor de Dados para uso no perfil MRTK
    - Habilitando o acompanhamento de olho no provedor olhar anexado à câmera
    - Configurando uma simulação de acompanhamento ocular no editor do Unity
    - Editar as funcionalidades da solução do Visual Studio para permitir o acompanhamento ocular no aplicativo criado

2. Adicione o componente de Destino de Acompanhamento Ocular aos objetos de destino. Para permitir que um objeto responda aos eventos olhar de olho, precisaremos adicionar o componente EyeTrackingTarget em cada objeto com o qual desejamos interagir usando o olho olhar. Adicione esse componente a cada um dos nove objetos 3D que fazem parte da coleção de grade.

    >[!TIP]
    >Você pode usar as teclas Shift e/ou CRTL para selecionar vários itens na hierarquia e, em seguida, adicionar o componente EyeTrackingTarget em massa.

    ![Lesson5 Chapter3 etapa 2](images/Lesson5Chapter3Step2.JPG)

3. Em seguida, adicionaremos o script EyeTrackingTutorialDemo para algumas interações empolgantes. Para cada objeto 3D na coleção de grade, adicione o script EyeTrackingTutorialDemo pesquisando o componente no menu Adicionar componente.

    ![Lesson5 Chapter3 etapa 3](images/Lesson5Chapter3Step3.JPG)

    >[!NOTE]
    >O material do script EyeTrackingTutorialDemo não faz parte do MRTK, mas está incluído com o ativo BaseModuleAssets importado na lição anterior.

4. Gire o objeto enquanto olha para o destino. Queremos configurar nossos objetos 3D para girar enquanto estamos examinando-os. Para fazer isso, insira um novo campo na seção ao examinar o destino () do componente EyeTrackingTarget, conforme mostrado na imagem abaixo.

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    No campo recém-criado, adicione o objeto de jogo atual ao campo vazio e selecione EyeTrackingTutorialDemo > RotateTarget (), conforme mostrado na imagem abaixo. Agora o objeto 3D está configurado para girar quando estiver sendo focado com o acompanhamento ocular.

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. Adicione a capacidade de "Blip Target" que está sendo gazedda ao selecionar por Air-TAP ou dizendo "Select". Semelhante à etapa 4, desejamos disparar EyeTrackingTutorialDemo > BlipTarget () atribuindo-o ao campo Select () do objeto Game do componente EyeTrackingTarget, conforme mostrado na figura abaixo. Com isso agora configurado, você notará um ligeiro blip no objeto Game sempre que disparar uma ação Select, como o Air-TAP ou o comando de voz "Select".

    ![Lesson5 Chapter3 Step5](images/Lesson5Chapter3Step5.JPG)

6. Certifique-se de que as funcionalidades de acompanhamento ocular estejam configuradas adequadamente antes de compilar para o HoloLens 2. No momento da redação deste artigo, o Unity ainda não tem a capacidade de definir a entrada olhar para recursos de acompanhamento de olho. A definição dessa funcionalidade é necessária para que o acompanhamento de olho funcione no HoloLens 2. Siga as instruções [testando seu aplicativo Unity em um HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) para habilitar o recurso de entrada olhar.

## <a name="congratulations"></a>Parabéns

Você adicionou com êxito os recursos básicos de acompanhamento de olho ao seu aplicativo. Essas ações são apenas o começo de um mundo de possibilidades com o acompanhamento ocular. Este capítulo também conclui a lição 5, na qual aprendemos sobre a funcionalidade de entrada avançada, como comandos de voz, gestos de panorâmica e acompanhamento de olho.

[Próxima lição: 7. criando um aplicativo de exemplo de módulo lunar](mrlearning-base-ch6.md)
