## <a name="lesson-2"></a>Lição 2

Na lição 2, vamos adicionar um modo Offline que nos permitirá executar a conversão de fala em texto local quando não é possível se conectar ao serviço do Azure e iremos *simular* um estado desconectado.

1. Selecione o objeto de "Lunarcom_Base" na hierarquia e clique em "Adicionar componente" no painel Inspetor. Pesquise e selecione o "reconhecimento Offline Lunarcom".

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)



2. Clique na lista suspensa no "LunarcomOfflineRecognizer" e selecione "Habilitado". Isso programará o projeto para atuar como o usuário não tem a conexão. 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. Agora, pressionar reproduzir no Editor do Unity e testá-lo. Pressione o microfone no canto inferior esquerdo da cena e começar a falar. 

> Observação: como estamos offline, a funcionalidade de ativação de Word foi desabilitada. Portanto, você terá que clique fisicamente o microfone toda vez que você deseja ter sua fala reconhecida enquanto offline. 

Abaixo está um exemplo de como poderia ser sua cena:

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>Parabéns

O modo offline foi ativado! Agora quando você estiver longe de qualquer forma de internet, você ainda pode trabalhar em seu projeto com o Speech SDK! 

[Próxima lição: SpeechSDK Lesson 3](link placeholder)

