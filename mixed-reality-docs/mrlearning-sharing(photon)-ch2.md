**Preparando para o desenvolvimento do Unity** 

Nesta lição, vamos aprenderá como preparar e configurar o Unity para desenvolvimento de aplicativos, incluindo importando o Kit de ferramentas de realidade misturada, definindo as configurações de compilação e preparando nossa cena.

Objetivos:

- Configurar o Unity para desenvolvimento de aplicativos

- Importe o Kit de ferramentas de realidade misturada

- Preparar sua cena do projeto

### <a name="instructions"></a>Instruções

1. Baixe e salve o pacote do Kit de ferramentas de realidade misturada unity clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)
2. No Unity, clique no menu de ativos e selecione "Importar pacote", clique em "Pacote personalizado".

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Selecione o pacote do Unity que você acabou de baixar o link fornecido na etapa 1. Quando aparece a janela pop-up da importação no Unity, clique no botão Importar para começar a importar. Importar o MRTK pode levar vários minutos.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> Observação: O pacote baixado será em sua pasta local onde você salvou o arquivo. A imagem acima não apresentação para onde você encontrará o pacote.

4. Crie uma nova cena (Isso pode ser feito clicando em "file" e selecionando "nova cena"). Salve a cena como "HLSharedProjectMain".

> Observação: você pode receber um pop-up que é semelhante à imagem a seguir. Por enquanto, basta clicar em "não".
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. Em, clique em "Toolkit de realidade mista" em "Adicionar à cena e configurar".

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Assim que estiver concluído, um novo arquivo de configuração será exibida, oferecendo a opção para personalizar o perfil. Clique em "copiar e personalizar."

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. Role para baixo e desmarque a opção "Habilitar sistema de diagnóstico" Se você quiser ocultar a janela de diagnóstico. É recomendável manter a janela de diagnóstico habilitados durante o desenvolvimento de aplicativo para monitorar o desempenho e desabilitá-lo durante as demonstrações de produção ou de aplicativo. 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Abra as configurações de build, pressionando CTRL + shift + B ou indo para arquivo > configurações de Build. Observe que o programa está atualmente definido na plataforma "PC, Mac e Linux autônomo". Para o desenvolvimento de 2 HoloLens, definir a plataforma para ser "Plataforma Universal do Windows." Selecione-o e clique em "alternar plataforma".![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. Uma vez concluído, clique na caixa que diz "Adicionar cenas abertas". Agora, vá para o painel do Inspetor e certifique-se de que a caixa de seleção à direita de "suportada de realidade virtual" (conforme mostrado na imagem abaixo) é verificada. Também Certifique-se de que a caixa de seleção ao lado de "cenas/HLSharedProjectMain" também é verificada, conforme mostrado na imagem abaixo.![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. Sob as "configurações de publicação" seção de rolagem do painel de inspetor para baixo até "Recursos" e certifique-se de que as seguintes caixas de seleção são marcadas:![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. Importar o pacote personalizado chamado "SharingAssetCollection", que pode ser baixado [aqui.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. Agora, no painel de projeto, vá para a pasta "pré-fabricados", já que nas próximas etapas você irá implementar alguns pré-fabricados na cena. Na pasta "pré-fabricados", clique e arraste pré-fabricado, "DebugWindow" na hierarquia. Quando terminar, salve o projeto (clique em arquivo, em seguida, salvar, ou pressione CTRL + S)

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > Observação: Você pode perceber um pop-up são exibidas à medida que você clicar no pré-fabricado, solicitando que você sobre o Essentials TMP. Clique em "Importar TMP Essentials" como eles serão necessários. Se essa janela pop-up aparecer, você talvez precise excluir pré-fabricado da sua hierarquia e arraste-o novamente na sua hierarquia para evitar possíveis erros relacionados ao texto.
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Parabéns

Seu projeto do Unity agora está pronto para Photon! Nas próximas lições, vamos compilar após esta cena e nosso projeto do Unity em direção uma experiência completa de compartilhado.

[Próxima lição: Sharing(Photon) lição 3](mrlearning-sharing(photon)-ch3.md)

