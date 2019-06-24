## <a name="lesson-4"></a>Lição 4

Capítulo 4, vamos explorar o recurso de intenção de serviços de fala. Nos conectamos irá configurar nosso Portal de LUIS do Azure, nossa intenção/entidades/declarações de instalação, publicar nosso recurso de intenção, nosso aplicativo Unity para nosso recurso de intenção e tornar nossa primeira chamada à API de intenção.

1. Permitir que seu computador habilitar o ditado, para fazer isso, vá para configurações do Windows, selecione "Privacidade", em seguida, "fala" e finalmente "escrita à tinta & digitando" e ative os serviços de fala e sugestões de digitação.

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> Observação: para obter informações sobre como fazer isso em um Mac/Macbook, clique em [aqui](linkgoeshere).

2. Faça logon na [Portal do Azure](https://portal.azure.com/). Quando você estiver conectado, clique em criar um recurso e pesquise por "Reconhecimento vocal" e clique em enter.

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. Selecione o botão Criar, para criar uma instância desse serviço. Nomeie o projeto "Speech_SDK_Learning_Module" e selecione "Pago conforme o uso."

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. Selecione sua região.  Para fins deste tutorial, selecione "(EUA) Oeste dos EUA". Em seguida, escolha "F0" para o tipo de preço. Agora clique em "criar" (localizado no canto inferior esquerdo) para criar o recurso.

   >  Observação: depois de clicar em "criar", você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

5. Uma notificação será exibida no portal depois que o recurso é criado. Clique nessa notificação e selecione "Ir para o recurso".

6. Na página "Início rápido" de seu serviço de "API do LUIS", navegue até a primeira etapa, pegue suas "chaves" e clique em "chaves" (você também pode fazer isso clicando no hiperlink azul "chaves", mostradas na imagem abaixo). Isso irá revelar o seu serviço, "Chaves". Salve uma cópia de uma das chaves para que você pode usá-lo mais tarde no aplicativo.

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. Volta na página "Início rápido" na seção 2b, clique em "Portal do reconhecimento vocal" (mostrado na imagem acima) para ser redirecionado à página da Web que você usará para criar seu novo serviço, dentro do aplicativo LUIS.

> Observação: Ao atingir o "Portal do reconhecimento vocal", você talvez precise fazer logon, se você não ainda estiverem, com as mesmas credenciais que o seu portal do Azure. Se essa for sua primeira vez usando o LUIS, você precisará rolar para baixo para a parte inferior da página de boas-vinda, para localizar e clique no botão "Criar LUIS" aplicativo.

8. Depois de conectado, clique em Meus aplicativos (se você não estiver nessa seção). Você pode clicar em criar novo aplicativo. Nomeie o novo aplicativo "Módulo de aprendizado de SDK da fala". Adicione "Módulo de aprendizado de SDK de fala" para o campo de descrição. Em seguida, clique em "concluído".

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> Observação: Se seu aplicativo deve para compreender um idioma diferente do inglês, você deve alterar a cultura"" para o idioma apropriado.

9. Clique em "Build", localizado no canto superior direito.

10. Em ativos de aplicativo à esquerda, selecione "Intenções", em seguida, clique em "Criar novo intenção" e nomeie-o "PressButton". 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> Observação: é importante usar os nomes das intenções e entidades usadas neste tutorial, porque o aplicativo Lunarcom referenciará-los por nome.  Para outros projetos, as convenções de nomenclatura podem ser tudo o que você escolher. 
>
> Observação: agora você deve ter 2 intenções - "PressButton" e "None".

11. Em ativos de aplicativo à esquerda, selecione "Entidades" e clique em "Criar nova entidade" e nomeie-a "Ação" e manter o tipo de entidade como "Simples".

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. Clique em "Criar nova entidade" novamente e nomeie-a "Destino" e manter o tipo de entidade como "Simples" também.

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. Em ativos de aplicativo à esquerda, selecione "Intenções" e clique em sua intenção de "PressButton" que você criou na etapa 10.

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. Clique no menu suspenso "Exibir opções" à direita e selecione "Mostrar valores de entidade". 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)Clique no "digite um exemplo..." caixa de texto. Em seguida, insira as seguintes declarações: 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. Clique no menu suspenso "Exibir opções" à direita e selecione "Mostrar nomes de entidade".

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. Certifique-se de que cada um a 10 declarações têm os seguintes rótulos de entidade nos locais a seguir por 1.) clicar em palavras que são rotulados de modo incorreto e, no pop-up, selecionando "remover o rótulo" e 2.) clicando em palavras que devem ser rotuladas e, no pop-up, selecionar o rótulo apropriado.

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. Agora, para publicar o modelo, clique em "Train" no canto superior direito. Depois que o processamento foi concluído, clique em "Test" no canto superior direito.

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. Insira "Selecionar o botão de inicialização" na caixa de texto.

> Observação: não adicionamos "selecionar" como uma ação em qualquer uma das nossas declarações - mas se você clicar em "Inspecionar", o modelo reconhecido "selecionar" como uma entidade de ação.
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. Agora, clique em "Publicar" no canto superior direito. Verifique se que a lista suspensa diz "Produção" e clique em "Publicar" o pop-up também. 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. Depois de publicado, uma barra verde deve aparecer na parte superior da página.  Clique na barra de verde para ser levado à página "Gerenciar". 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. Clique em "Chaves e pontos de extremidade" em "Configurações de aplicativo" à esquerda. Em seguida, defina a lista suspensa "Publish To" como "Produção". Definir o fuso horário para corresponder às suas e marque a caixa para incluir todas as pontuações previstas de intenção. Por fim, clique em "Atribuir recursos".

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. Selecione o locatário na primeira lista suspensa e selecione "Pré-pago" no menu suspenso o nome da assinatura. Em nome do recurso LUIS, escolha o recurso que criamos acima nas etapas 1 a 5. Em seguida, clique em "Atribuir recursos". 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> Observação: Certifique-se de copiar e salvar a URL de ponto de extremidade associado ao recurso que atribuímos apenas para que ele seja facilmente acessível para a próxima seção.
>
> Observação: para o nome do locatário, colocar sua empresa ou o perfil que você criou para este aplicativo.

23. Agora, abra o novo aplicativo no Unity e selecione o objeto Lunarcom_Base na hierarquia. Clique em "Adicionar componente" no painel Inspetor, pesquise e selecione "LunarcomIntentRecognizer".

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. No campo de "LunarcomIntentRecognizer" no painel Inspetor Luis Endpoint, insira a URL de ponto de extremidade que você salvou na etapa 22. 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  Observação: No componente "LunarcomOfflineRecognizer" no painel Inspetor, certifique-se de que "Desabilitar" está selecionado para "SimulateOfflineMode" caso contrário, o programa de teste não funcionará. 

25. Pressione o botão Reproduzir no Editor do Unity e clique no botão de rocket para iniciar o reconhecimento de intenção. Emitido a frase "Selecionar o botão de bicho de inicialização".

>  Observação: O aplicativo reconhecido na função desejada e ativado no botão dos rocket.
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Parabéns

Oficialmente, você aprendeu como adicionar comandos de fala do programa fala SDK! Agora seu programa possa reconhecer os comandos de fala de todos os tipos de variantes. Testá-lo e se divertir um pouco com ele!

[Próxima lição: SDK de fala lição 5](placeholderlink)

