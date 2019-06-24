# <a name="speech-sdk-learning-module"></a>Módulo de aprendizagem do SDK de fala

Neste tutorial, você criará um aplicativo de realidade mista que explora o uso de fala SDK dos serviços Cognitivos do Azure com o HoloLens 2. Quando terminar com esta série de tutoriais, você poderá usar o microfone do dispositivo para transcrever o reconhecimento de fala em tempo real, traduzir a fala para outros idiomas e aproveite o recurso de intenção de fala do SDK para entender os comandos de voz usando inteligência artificial.

Objetivos:

- Aprenda a integrar o SDK do Azure de fala em um aplicativo do HoloLens 2
- Saiba como usar comandos de voz
- Saiba como usar os recursos de fala em texto

## <a name="instructions"></a>Instruções

### <a name="getting-started"></a>Introdução

1. Inicie o Unity e crie um novo projeto. Insira o nome do projeto "Módulo de aprendizado de SDK da fala". Escolha um local para onde salvar o seu projeto. Em seguida, clique em "Criar projeto".

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> Observação: Certifique-se de que o modelo é definido como "3D", conforme mostrado na imagem acima.

2. Baixe o [Kit de ferramentas de realidade misturada](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity empacotar e salvá-lo em uma pasta em seu computador. Importe o pacote para seu projeto do Unity. Para obter instruções detalhadas sobre como fazer isso, consulte [lição 1 para o módulo básico](mrlearning-base-ch1.md). 

3. Baixar e importar do Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) para pacote de ativos do Unity. Importar o pacote SDK de fala, clicando em "ativos", selecionando "Importar pacote", em seguida, selecionando o "pacote personalizado". Localize o pacote do SDK de fala que baixou anteriormente e abri-lo para começar o processo de importação. 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. Na próxima janela pop-up, clique em "Importar" para começar a importar o pacote SDK de fala. Verifique se que todos os itens são verificados, conforme mostrado na imagem abaixo.

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. Baixe o [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) pacote ativo. O pacote de ativos Lunarcom é uma coleção de ativos e scripts desenvolvidos para esta série de lição para demonstrar um uso prático do SDK de fala do Azure. É um terminal de comando de voz, por fim, interagirá com a experiência de assembly de módulo lunar desenvolvida no [Tutorial do módulo de Base.](mrlearning-base-ch6.md)
6. Importe o pacote de ativos de Lunarcom para seu projeto do Unity seguindo as etapas semelhantes que levou para importar o Kit de ferramentas de realidade mista e o SDK de fala.
7. Configure o Kit de ferramentas de realidade misturada (MRTK). Para fazer isso, clique no painel de "Toolkit de realidade mista" na parte superior da sua janela e, em seguida, selecione "Adicionar a cena e configurar".

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. Sua cena agora terá vários novos itens do que o MRTK. Salve sua cena com um nome diferente clicando em "file", em seguida, "Salvar como" e nomeie sua cena "SpeechScene". 

   > Observação: Se você pressionar o botão Reproduzir em sua cena depois de adicionar o MRTK ao seu projeto, e ele não entra no modo de "reproduzir", você talvez precise reiniciar o Unity. 

9. Com o objeto de "MixedRealityToolkit" selecionado na sua hierarquia, clique em "copiar e personalizar" no painel Inspetor.

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. Também no painel Inspetor (com o objeto de "MixedRealityToolkit" selecionado na hierarquia), desabilite o sistema de diagnóstico, desmarcando a caixa à direita de "Habilitar sistema de diagnóstico".

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. No painel de projeto, expanda a pasta "Lunarcom" e arraste pré-fabricado "Lunarcom_Base" em sua hierarquia.

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. Selecione o objeto de "Lunarcom_Base" em sua hierarquia e certifique-se de que a posição é definida como x = 0, y = 0 e z = 0, bem como a rotação definida como x = 0, y = 0 e z = 0. Defina a escala para ler x = 0,008, y = 0,008 e z = 0,01.

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. Clique em "adicionar o componente", pesquise e selecione "LunarcomController". Esse script está incluído no pacote de ativo Lunarcom importado na etapa 6.

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. Para conectar nosso aplicativo de serviços Cognitivos do Azure, você deve inserir uma "chave de assinatura" também conhecido como "Chave API" para o serviço de fala. Siga as instruções em [esse link](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) para obter uma chave de assinatura gratuita. Depois de obter a chave de assinatura, insira-o no campo "Chave de API de serviço de fala" do componente "LunarcomController" no painel de Inspetor, conforme mostrado na imagem abaixo.

15. Insira a região que você escolheu quando se inscreveu para a chave de assinatura no campo "Região do serviço de fala" do componente "LunarcomController" no painel Inspetor.

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. Em sua hierarquia, expanda o objeto "Lunarcom_Base" clicando na seta à esquerda dela e fazer o mesmo para seu objeto filho, "Terminal", conforme mostrado na imagem abaixo.

17. Enquanto "Lunarcom_Base" estiver selecionado, clique e arraste "Lunarcom texto" da hierarquia para o slot de "Texto de saída" no componente "LunarcomController" no painel Inspetor, conforme mostrado na imagem abaixo.
18. Agora, fazer a mesma coisa com o objeto "Terminal" no slot de "terminal" e o objeto "Conexão Light" para o slot de "Conexão luz Controller".

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. Clique na seta ao lado da seção "Lunarcom botões" do script "LunarcomController" no painel Inspetor e alterar o tamanho para 3 e pressione a tecla Enter ou Return no seu teclado. Isso fará com que três novos campos "Element" apareça.

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. Expanda os "botões Lunarcom" clicando na seta ao lado na sua hierarquia e, usando o mesmo processo que o descrito acima, arraste o Mic e satélite Rocket gameobjects as referências de elemento 0, 1 e 2, respectivamente, no componente "LunarcomController" no painel do Inspetor. 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. Selecione o objeto de "Lunarcom_Base" em sua hierarquia. Clique em "Adicionar componente" no painel Inspetor, pesquise e selecione "LunarcomWakeWordRecognizer".

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. No slot de "Wake Word", digite "Ativar Terminal". Além disso, no slot de "Ignorar a palavra", digite "Ignorar Terminal".

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a>Parabéns

Você configurou o reconhecimento de voz em seu aplicativo, da plataforma Azure! Execute o aplicativo para garantir que todas as funções estão funcionando corretamente. Comece informando que a palavra de ativação que você digitou na etapa 22, "Ativar Terminal". Em seguida, selecione o botão de microfone para iniciar o reconhecimento de voz e começar a falar. Você verá as palavras transcrita no terminal enquanto fala. Pressione o botão de microfone uma segunda vez para parar o reconhecimento de voz. Digamos que "Descartar Terminal" para ocultar o terminal Lunarcom. Na próxima lição, aprenderemos como alternar dinamicamente para usar o reconhecimento de voz baseados em dispositivo, para situações em que o SDK da fala do Azure não está disponível devido ao 2 HoloLens offline.

[Próxima lição: SDK de fala lição 2](mrlearning-speechSDK-ch2.md)

