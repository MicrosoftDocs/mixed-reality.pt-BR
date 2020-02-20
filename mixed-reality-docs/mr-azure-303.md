---
title: Sr e Azure 303 – LUIS (reconhecimento de linguagem natural)
description: Conclua este curso para aprender a implementar o LUIS (serviço do Azure Reconhecimento vocal Intelligence) em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, serviço de inteligência de reconhecimento de linguagem, Luis, hololens, imersão, VR
ms.openlocfilehash: 9b3e4f081dc8a054d783246554f904a38f43f26c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926811"
---
>[!NOTE]
>Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>Sr e Azure 303: LUIS (reconhecimento de linguagem natural)

Neste curso, você aprenderá a integrar o Reconhecimento vocal a um aplicativo de realidade misturada usando os serviços cognitivas do Azure, com o API de Reconhecimento Vocal.

![Resultado do laboratório](images/AzureLabs-Lab3-000.png)

O *reconhecimento vocal (Luis)* é um serviço Microsoft Azure, que fornece aos aplicativos a capacidade de fazer o significado da entrada do usuário, como por meio da extração do que uma pessoa pode querer, em suas próprias palavras. Isso é obtido por meio do aprendizado de máquina, que compreende e aprende as informações de entrada e, em seguida, pode responder com informações detalhadas e relevantes. Para obter mais informações, visite a [página reconhecimento vocal do Azure (Luis)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).

Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada que poderá fazer o seguinte:

1.  Capture a fala de entrada do usuário, usando o microfone anexado ao headset de imersão. 
2.  Enviar o ditado capturado do *serviço inteligente de reconhecimento vocal do Azure* (*Luis*). 
3.  Faça com que o LUIS extra o significado das informações de envio, que serão analisadas, e a tentativa de determinar a intenção da solicitação do usuário será feita.

O desenvolvimento incluirá a criação de um aplicativo em que o usuário poderá usar voz e/ou olhar para alterar o tamanho e a cor dos objetos na cena. O uso de controladores de movimento não será abordado.

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.

Esteja preparado para treinar o LUIS várias vezes, que é abordado no [capítulo 12](#chapter-12--improving-your-luis-service). Você obterá resultados melhores, mais vezes o LUIS foi treinado.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Sr e Azure 303: LUIS (reconhecimento de linguagem natural)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens. Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens. Ao usar o HoloLens, você pode notar um eco durante a captura de voz.

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

> [!NOTE]
> Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018). Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)
- [Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md)
- [O SDK do Windows 10 mais recente](install-the-tools.md)
- [Unity 2017,4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado
- Um conjunto de fones de ouvido com um microfone interno (se o headset não tiver um MIC interno e alto-falantes)
- Acesso à Internet para a instalação do Azure e recuperação LUIS

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação). 
2.  Para permitir que o computador habilite o ditado, acesse **as configurações do Windows > privacidade > fala, digitando a tinta & digitar** e pressione o botão **ativar os serviços de fala e digitar sugestões**.
3.  O código neste tutorial permitirá que você registre a partir do conjunto de **dispositivos do microfone padrão** em seu computador. Verifique se o dispositivo de microfone padrão está definido como aquele que você deseja usar para capturar sua voz.
4.  Se o headset tiver um microfone interno, certifique-se de que a opção *"quando eu utilizo meu Headset, mude para MIC do headset"* esteja ativada nas configurações do *portal da realidade misturada* .

    ![Configurando o headset de imersão](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Capítulo 1 – configurar o portal do Azure

Para usar o serviço de *reconhecimento vocal* no Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.

1.  Faça logon no [portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *reconhecimento vocal*e clique em **Enter**. 

    ![Criar recurso LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.
 
3.  A nova página à direita fornecerá uma descrição do serviço Reconhecimento vocal. Na parte inferior esquerda desta página, selecione o botão **criar** para criar uma instância desse serviço.

    ![Criação de serviço LUIS-aviso legal](images/AzureLabs-Lab3-02.png)
 
4.  Depois de clicar em criar:

    1. Insira o **nome** desejado para esta instância de serviço.
    2. Selecione uma **assinatura**.
    3. Selecione o **tipo de preço** apropriado para você, se esta for a primeira vez que criar um *serviço Luis*, uma camada gratuita (chamada F0) deverá estar disponível para você. A alocação gratuita deve ser mais do que suficiente para este curso.
    4. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.
    6. Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.
    7. Selecione **Criar**.

        ![Criar serviço LUIS-entrada do usuário](images/AzureLabs-Lab3-03.png)
 
5.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.
6.  Uma notificação será exibida no portal assim que a instância do serviço for criada. 
 
    ![Nova imagem de notificação do Azure](images/AzureLabs-Lab3-04.png)

7.  Clique na notificação para explorar sua nova instância de serviço.

    ![Notificação de criação de recursos bem-sucedida](images/AzureLabs-Lab3-05.png)
 
8.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. Você será levado à sua nova instância do serviço LUIS. 
 
    ![Acessando chaves LUIS](images/AzureLabs-Lab3-06.png)

9.  Neste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, o que é feito por meio do uso da chave de assinatura do serviço.
10. Na página *início rápido* , do serviço *API do Luis* , navegue até a primeira etapa, *pegue as chaves*e clique em **chaves** (você também pode fazer isso clicando nas teclas de hiperlink azul, localizadas no menu de navegação serviços, indicado pelo ícone de chave). Isso revelará suas *chaves*de serviço.
11. Faça uma cópia de uma das chaves exibidas, pois você precisará dela posteriormente em seu projeto. 
12. Na página *serviço* , clique em *reconhecimento vocal portal* para ser redirecionado para a página da Web que você usará para criar seu novo serviço, dentro do aplicativo Luis. 

## <a name="chapter-2--the-language-understanding-portal"></a>Capítulo 2 – o portal de Reconhecimento vocal

Nesta seção, você aprenderá a criar um aplicativo LUIS no portal do LUIS. 

> [!IMPORTANT]
> Esteja ciente de que a configuração de *entidades*, *intenções*e *declarações* dentro deste capítulo é apenas a primeira etapa na criação do seu serviço Luis: você também precisará treinar novamente o serviço, várias vezes, para torná-lo mais preciso. O novo treinamento do seu serviço é abordado no [último capítulo](#chapter-12--improving-your-luis-service) deste curso, portanto, certifique-se de concluí-lo.

1.  Ao atingir o *portal de reconhecimento vocal*, talvez seja necessário fazer logon, se você ainda não tiver, com as mesmas credenciais que o portal do Azure. 

    ![Página de logon do LUIS](images/AzureLabs-Lab3-07.png)
 
2.  Se esta for a primeira vez que você usa o LUIS, você precisará rolar para baixo até a parte inferior da página de boas-vindas, para localizar e clicar no botão **criar aplicativo Luis** .

    ![Página criar aplicativo LUIS](images/AzureLabs-Lab3-08.png)
 
3.  Depois de conectado, clique em **meus aplicativos** (se você não estiver na seção no momento). Em seguida, você pode clicar em **criar novo aplicativo**.

    ![LUIS-imagem de meus aplicativos](images/AzureLabs-Lab3-09.png)
 
4.  Dê um *nome*ao seu aplicativo.
5.  Se seu aplicativo deve entender uma linguagem diferente do inglês, você deve alterar a *cultura* para o idioma apropriado.
6.  Aqui você também pode adicionar uma *Descrição* do seu novo aplicativo Luis.

    ![LUIS-criar um novo aplicativo](images/AzureLabs-Lab3-10.png)

7.  Depois de pressionar **concluído**, você vai inserir a página de *compilação* do seu novo aplicativo *Luis* .
8.  Há alguns conceitos importantes a serem compreendidos aqui:

    -   *Intenção*, representa o método que será chamado após uma consulta do usuário. Uma *intenção* pode ter uma ou mais *entidades*.
    -   *Entidade*, é um componente da consulta que descreve as informações relevantes para a *intenção*.
    -   *Declarações*, são exemplos de consultas fornecidas pelo desenvolvedor, que o Luis usará para se treinar.

Se esses conceitos não estiverem perfeitamente claros, não se preocupe, pois este curso os esclarecerá ainda mais neste capítulo.

Você começará criando as *entidades* necessárias para compilar este curso.

9.  No lado esquerdo da página, clique em *entidades*e, em seguida, clique em **criar nova entidade**.

    ![Criar nova entidade](images/AzureLabs-Lab3-11.png)

10. Chame a nova *cor*da entidade, defina seu tipo como *simples*e pressione **concluído**.

    ![Criar entidade-cor simples](images/AzureLabs-Lab3-12.png)
 
11. Repita esse processo para criar três (3) entidades mais simples chamadas:

    -   *ampliar*
    -   *diminuir*
    -   *alvo*

O resultado deve ser semelhante à imagem abaixo:

![Resultado da criação de entidade](images/AzureLabs-Lab3-13.png)
 
Neste ponto, você pode começar a criar *tentativas*. 

> [!WARNING]
> Não exclua a tentativa **nenhum** .

12. No lado esquerdo da página, clique em **tentativas**e, em seguida, clique em **criar nova tentativa**.

    ![Criar novas tentativas](images/AzureLabs-Lab3-14.png)

13. Chame a nova *intenção* **ChangeObjectColor**.

    > [!IMPORTANT]
    > Esse nome de *intenção* é usado no código posteriormente neste curso, para obter melhores resultados, use esse nome exatamente como fornecido.

Depois de confirmar o nome, você será direcionado para a página de tentativas.

![LUIS – página de intenções](images/AzureLabs-Lab3-15.png)

Você observará que há uma caixa de texto solicitando que você digite 5 ou mais *declarações*diferentes.

> [!NOTE]
> LUIS converte todas as declarações em minúsculas.

14. Insira o seguinte *expressão* na caixa de texto superior (atualmente, com o tipo de texto *cerca de 5 exemplos...* ) e pressione **Enter**:

```
The color of the cylinder must be red
```

Você notará que o novo *expressão* aparecerá em uma lista abaixo.

Seguindo o mesmo processo, insira os seis (6) declarações a seguir:

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Para cada expressão que você criou, você deve identificar quais palavras devem ser usadas pelo LUIS como entidades. Neste exemplo, você precisa rotular todas as cores como uma entidade de *cor* e toda a referência possível a um destino como uma entidade de *destino* .

15. Para fazer isso, tente clicar no *cilindro* de palavras na primeira expressão e selecionar *destino*.

    ![Identificar destinos de expressão](images/AzureLabs-Lab3-16.png)
 
16. Agora, clique na palavra *vermelho* na primeira expressão e selecione *cor*.

    ![Identificar entidades expressão](images/AzureLabs-Lab3-17.png)
 
17. Rotule a próxima linha também, onde o *cubo* deve ser um *destino*e *preto* deve ser uma *cor*. Observe também o uso das palavras *' this '* , *' it '* e *' this Object '* , que estamos fornecendo, por isso também há tipos de destino não específicos disponíveis. 

18. Repita o processo acima até que todos os declarações tenham as entidades rotuladas. Consulte a imagem abaixo se precisar de ajuda.

    > [!TIP]
    > Ao selecionar palavras para rotulá-las como entidades:
    > - Para palavras únicas, basta clicar nelas.
    > - Para um conjunto de duas ou mais palavras, clique no início e, em seguida, no final do conjunto.

    > [!NOTE]
    > Você pode usar o botão de alternância de *exibição de tokens* para alternar entre a **exibição de entidades/tokens**!

19. Os resultados devem ser mostrados nas imagens abaixo, mostrando a **exibição de entidades/tokens**:

    ![Exibições & entidades de tokens](images/AzureLabs-Lab3-18.png)
  
20. Neste ponto, pressione o botão **treinar** na parte superior direita da página e aguarde até que o pequeno indicador de ida e volta fique verde. Isso indica que o LUIS foi treinado com êxito para reconhecer essa intenção.

    ![Treinar o LUIS](images/AzureLabs-Lab3-19.png)
 
21. Como um exercício para você, crie uma nova tentativa chamada **ChangeObjectSize**, usando as entidades *target*, *upsize*e *diminuir*.
22. Seguindo o mesmo processo que a intenção anterior, insira as oito (8) declarações a seguir para alterar o *tamanho* :

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. O resultado deve ser semelhante ao mostrado na imagem abaixo:

    ![Configurar os tokens/entidades do ChangeObjectSize](images/AzureLabs-Lab3-20.png) 

24. Depois que as tentativas, **ChangeObjectColor** e **ChangeObjectSize**forem criadas e treinadas, clique no botão **publicar** na parte superior da página.

    ![Publicar serviço LUIS](images/AzureLabs-Lab3-21.png)

25. Na página de *publicação* , você finalizará e publicará seu aplicativo Luis para que ele possa ser acessado pelo seu código.

    1. Defina a lista suspensa *publicar* como **produção**.
    2. Defina o *fuso horário* para seu fuso horário.
    3. Marque a caixa **incluir todas as pontuações de intenção prevista**.
    4. Clique em **publicar no slot de produção**.

        ![Publicar configurações](images/AzureLabs-Lab3-22.png)

26. Na seção *recursos e chaves*:

    1.  Selecione a região que você definiu para a instância de serviço no portal do Azure.
    2.  Você observará um elemento **Starter_Key** abaixo, ignorará-o.
    3.  Clique em **Adicionar chave** e insira a *chave* que você obteve no portal do Azure quando você criou sua instância de serviço. Se o Azure e o portal do LUIS estiverem conectados ao mesmo usuário, serão fornecidos menus suspensos para *nome do locatário*, nome da *assinatura*e a *chave* que você deseja usar (terá o mesmo nome fornecido anteriormente no portal do Azure.

    > [!IMPORTANT] 
    > Sob o *ponto de extremidade*, faça uma cópia do ponto de extremidade correspondente à chave que você inseriu, em breve, você o usará em seu código.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Capítulo 3 – configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com a realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o *Unity* e clique em **novo**. 

    ![Inicie o novo projeto do Unity.](images/AzureLabs-Lab3-24.png)

2.  Agora será necessário fornecer um nome de projeto de Unity, inserir **MR_LUIS**. Verifique se o tipo de projeto está definido como **3D**. Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab3-25.png)
 
3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para editar preferências de > e, em seguida, na nova janela, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio 2017**. Feche a janela **preferências** .

    ![Atualize a preferência do editor de script.](images/AzureLabs-Lab3-26.png)
 
4.  Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma para **plataforma universal do Windows**clicando no botão **alternar plataforma** .

    ![Janela de configurações de compilação, alterne a plataforma para UWP.](images/AzureLabs-Lab3-27.png)
 
5.  Vá para **arquivo > configurações de compilação** e verifique se:

    1. O **dispositivo de destino** está definido para **qualquer dispositivo**

        > Para o Microsoft HoloLens, defina o **dispositivo de destino** como *HoloLens*.

    2. O **tipo de compilação** está definido como **D3D**
    3. O **SDK** está definido para o **mais recente instalado**
    4. A **versão do Visual Studio** está definida para o **mais recente instalado**
    5. **Compilar e executar** é definido como **computador local**
    6. Salve a cena e adicione-a à compilação.

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.
        
            ![Clique no botão Adicionar cenas abertas](images/AzureLabs-Lab3-28.png)

        2. Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![Criar nova pasta de scripts](images/AzureLabs-Lab3-29.png)

        3. Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo*:, digite **MR_LuisScene**e pressione **salvar**.

            ![Dê um nome à nova cena.](images/AzureLabs-Lab3-30.png)

    7. As configurações restantes, em *configurações de compilação*, devem ser deixadas como padrão por enquanto.

6. Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado. 

    ![Abra as configurações do Player.](images/AzureLabs-Lab3-31.png) 
 
7. Nesse painel, algumas configurações precisam ser verificadas:

    1. Na guia **outras configurações** :

        1. A **versão de tempo de execução de script** deve ser **estável** (.net 3,5 equivalente).
        2. O **back-end de script** deve ser **.net**
        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![Atualize outras configurações.](images/AzureLabs-Lab3-32.png)
      
    2. Na guia **configurações de publicação** , em **recursos**, marque:

        1. **InternetClient**
        2. **Phone**

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab3-33.png)

    3. Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o **SDK do Windows Mixed Reality** foi adicionado.

        ![Atualize as configurações de X R.](images/AzureLabs-Lab3-34.png)

8.  De volta *às configurações de Build* , os projetos do  _C# Unity_ não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste. 
9.  Feche a janela configurações de compilação.
10. Salve sua cena e projeto (**arquivo > salvar cena/arquivo > salvar projeto**).

## <a name="chapter-4--create-the-scene"></a>Capítulo 4 – criar a cena

> [!IMPORTANT]
> Se você quiser ignorar o componente *de configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para baixar esse [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importe-o para seu projeto como um [pacote personalizado](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue no [capítulo 5](#chapter-5--create-the-microphonemanager-class). 

1.  Clique com o botão direito do mouse em uma área vazia do *painel hierarquia*, em **objeto 3D**, adicione um **plano**.

    ![Crie um plano.](images/AzureLabs-Lab3-35.png)

2.  Lembre-se de que, ao clicar com o botão direito do mouse na *hierarquia* novamente para criar mais objetos, se você ainda tiver o último objeto selecionado, o objeto selecionado será o pai do novo objeto. Evite clicar em um espaço vazio dentro da hierarquia e clicar com o botão direito do mouse.

3.  Repita o procedimento acima para adicionar os seguintes objetos:

    1. *Esfera*
    2. *Tubo*
    3. *Simples*
    4. *Texto 3D*

4.  A *hierarquia* de cena resultante deve ser parecida com a da imagem abaixo:

    ![Configuração da hierarquia de cena.](images/AzureLabs-Lab3-36.png)
 
5.  Clique com o botão esquerdo na **câmera principal** para selecioná-lo, examine o *painel Inspetor* . você verá o objeto Camera com todos os seus componentes.
6.  Clique no botão **Adicionar componente** localizado na parte inferior do *painel Inspetor*.

    ![Adicionar fonte de áudio](images/AzureLabs-Lab3-37.png)
 
7.  Pesquise o componente chamado *fonte de áudio*, conforme mostrado acima.
8.  Além disso, verifique se o componente de *transformação* da câmera principal está definido como (0, 0, 0). isso pode ser feito pressionando o ícone de **engrenagem** ao lado do componente de *transformação* da câmera e selecionando **Redefinir**. O componente de *transformação* deve ter a seguinte aparência:

    1.  A *posição* é definida como **0, 0,** 0.
    2.  A *rotação* está definida como **0, 0, 0**.

    > [!NOTE] 
    > Para o Microsoft HoloLens, você também precisará alterar o seguinte, que fazem parte do componente da **câmera** , que está em sua **câmera principal**:
    > - **Limpar sinalizadores:** Cor sólida.
    > - **Plano de fundo** ' Black, Alpha 0 ' – cor hexadecimal: #00000000.

9.  Clique com o botão esquerdo do **plano** para selecioná-lo. No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:

    |       | Transformação- *posição* |       |
    |:-----:|:----------------------:|:-----:|
    | **W.x.y.** | **Iar**                  | **Z** |
    | 0     | -1                     | 0     |


10. Clique com o botão esquerdo do **círculo** para selecioná-lo. No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:

    |       | Transformação- *posição* |       |
    |:-----:|:----------------------:|:-----:|
    | **W.x.y.** | **Iar**                  | **Z** |
    | 2     | 1                      | 2     |

11. Clique com o botão esquerdo do **cilindro** para selecioná-lo. No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:

    |       | Transformação- *posição* |       |
    |:-----:|:----------------------:|:-----:|
    | **W.x.y.** | **Iar**                  | **Z** |
    | -2    | 1                      | 2     |

12. Clique com o botão esquerdo do **cubo** para selecioná-lo. No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:

    |        | Transformação- *posição* |       |  \| |       | Transformação- *rotação* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **W.x.y.** | **Iar**                   | **Z** |  \| | **W.x.y.** | **Iar**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Clique no botão esquerdo do novo objeto de **texto** para selecioná-lo. No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:

    |       | Transformação- *posição* |       |  \| |       | Transformar em *escala* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **W.x.y.** | **Iar**                  | **Z** |  \| | **W.x.y.** | **Iar**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0,1   | 0,1                 | 0,1   | 

14. Altere o **tamanho da fonte** no componente de malha de **texto** para **50**.
15. Altere o *nome* do objeto de **malha de texto** para texto de **ditado**.

    ![Criar objeto de texto 3D](images/AzureLabs-Lab3-38.png)
 
16. A estrutura do painel de hierarquia agora deve ser assim:

    ![malha de texto na exibição de cena](images/AzureLabs-Lab3-38b.png)


17. A cena final deve ser parecida com a imagem abaixo:

    ![A exibição de cena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Capítulo 5 – criar a classe microphonemanager

O primeiro script que você pretende criar é a classe *microphonemanager* . Depois disso, você criará o *LuisManager*, a classe de *comportamentos* e, por fim, a classe *olhar* (fique à vontade para criar todos eles agora, embora ele seja coberto à medida que você atingir cada capítulo).

A classe *microphonemanager* é responsável por:

-   Detectando o dispositivo de gravação conectado ao headset ou ao computador (o que for o padrão).
-   Capture o áudio (voz) e use o ditado para armazená-lo como uma cadeia de caracteres.
-   Depois que a voz for pausada, envie o ditado para a classe *LuisManager* . 

Para criar esta classe: 

1.  Clique com o botão direito do mouse no *painel Projeto*, **crie > pasta**. Chame os **scripts**da pasta. 

    ![Criar pasta de scripts.](images/AzureLabs-Lab3-40.png)
 
2.  Com a pasta **scripts** criada, clique duas vezes nela para abrir. Em seguida, dentro dessa pasta, clique com o botão direito do mouse em **criar > C# script**. Nomeie o script *microphonemanager*. 

3.  Clique duas vezes em *microfonemanager* para abri-lo com o *Visual Studio*.
4.  Adicione os seguintes namespaces à parte superior do arquivo:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro da classe *microphonemanager* :

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  O código para os métodos *ativo ()* e *Iniciar ()* agora precisa ser adicionado. Eles serão chamados quando a classe for inicializada:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  Agora você precisa do método que o aplicativo usa para iniciar e parar a captura de voz e passá-la para a classe *LuisManager* , que será criada em breve. 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  Adicione um *manipulador de ditado* que será invocado quando a voz pausar. Esse método passará o texto do ditado para a classe *LuisManager* .

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > Exclua o método *Update ()* , pois essa classe não o usará.

9.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

    > [!NOTE]
    > Neste ponto, você observará um erro exibido no *painel de console do editor do Unity*. Isso ocorre porque o código faz referência à classe *LuisManager* , que você criará no próximo capítulo.

## <a name="chapter-6--create-the-luismanager-class"></a>Capítulo 6 – criar a classe LUISManager

É hora de criar a classe *LuisManager* , que fará a chamada para o serviço Luis do Azure. 

A finalidade dessa classe é receber o texto do ditado da classe *microphonemanager* e enviá-lo para o *API de reconhecimento vocal do Azure* a ser analisado.

Essa classe desserializará a resposta *JSON* e chamará os métodos apropriados da classe de *comportamentos* para disparar uma ação.

Para criar esta classe: 

1.  Clique duas vezes na pasta **scripts** para abri-la. 
2.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**. Nomeie o script *LuisManager*. 
3.  Clique duas vezes no script para abri-lo com o Visual Studio.
4.  Adicione os seguintes namespaces à parte superior do arquivo:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Você começará criando três classes **dentro** da classe *LuisManager* (dentro do mesmo arquivo de script, acima do método *Start ()* ) que representará a resposta JSON desserializada do Azure.

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  Em seguida, adicione as seguintes variáveis dentro da classe *LuisManager* :
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Certifique-se de colocar seu ponto de extremidade do LUIS agora (que você terá do seu portal do LUIS).

8.  O código para o método *ativo ()* agora precisa ser adicionado. Esse método será chamado quando a classe inicializar:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  Agora você precisa dos métodos que esse aplicativo usa para enviar o ditado recebido da classe *microphonemanager* para *Luis*e, em seguida, receber e desserializar a resposta. 
10. Depois que o valor da intenção e as entidades associadas forem determinados, eles serão passados para a instância da classe de *comportamentos* para disparar a ação pretendida.

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. Crie um novo método chamado *AnalyseResponseElements ()* que lerá o *AnalysedQuery* resultante e determine as entidades. Depois que essas entidades forem determinadas, elas serão passadas para a instância da classe de *comportamentos* a ser usada nas ações.

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > Exclua os métodos *Start ()* e *Update ()* , pois essa classe não os usará.

12. Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

> [!NOTE]
> Neste ponto, você observará que vários erros aparecem no *painel de console do editor do Unity*. Isso ocorre porque o código faz referência à classe de *comportamentos* que você criará no próximo capítulo.

## <a name="chapter-7--create-the-behaviours-class"></a>Capítulo 7 – criar a classe de comportamentos

A classe de *comportamentos* irá disparar as ações usando as entidades fornecidas pela classe *LuisManager* .

Para criar esta classe: 

1.  Clique duas vezes na pasta **scripts** para abri-la. 
2.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**. Nomeie os *comportamentos*do script. 
3.  Clique duas vezes no script para abri-lo com o *Visual Studio*.
4.  Em seguida, adicione as seguintes variáveis dentro da classe de *comportamentos* :

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Adicione o código do método *ativo ()* . Esse método será chamado quando a classe inicializar:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  Os métodos a seguir são chamados pela classe *LuisManager* (que você criou anteriormente) para determinar qual objeto é o destino da consulta e, em seguida, disparar a ação apropriada.

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  Adicione o método *FindTarget ()* para determinar qual *Gameobjects* é o destino da tentativa atual. Esse método padroniza o destino para o *gameobject* como "gazed" se nenhum destino explícito for definido nas entidades.

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > Exclua os métodos *Start ()* e *Update ()* , pois essa classe não os usará.

8.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-8--create-the-gaze-class"></a>Capítulo 8 – criar a classe olhar

A última classe que será necessária para concluir esse aplicativo é a classe *olhar* . Essa classe atualiza a referência ao *gameobject* no momento no foco visual do usuário.

Para criar esta classe: 

1.  Clique duas vezes na pasta **scripts** para abri-la. 
2.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**. Nomeie o script *olhar*. 
3.  Clique duas vezes no script para abri-lo com o *Visual Studio*.
4.  Insira o seguinte código para esta classe:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-9--completing-the-scene-setup"></a>Capítulo 9 – concluindo a configuração da cena

1.  Para concluir a configuração da cena, arraste cada script que você criou da pasta scripts para o objeto da **câmera principal** no *painel hierarquia*.
2.  Selecione a **câmera principal** e examine o *painel Inspetor*, você deve ser capaz de ver cada script que você anexou e observará que há parâmetros em cada script que ainda devem ser definidos.

    ![Definindo os destinos de referência da câmera.](images/AzureLabs-Lab3-41.png)

3.  Para definir esses parâmetros corretamente, siga estas instruções:

    1. *Microfonemanager*:

        - No *painel hierarquia*, arraste o objeto de **texto ditado** para a caixa valor do parâmetro **texto do ditado** .

    2. *Comportamentos*, no *painel hierarquia*:

        - Arraste o objeto de **esfera** para a caixa destino de referência de *esfera* .
        - Arraste o **cilindro** para a caixa destino de referência do *cilindro* .
        - Arraste o **cubo** para a caixa destino de referência do *cubo* .

    3. *Olhar*:

        - Defina a *distância máxima olhar* como **300** (se ainda não estiver). 

4.  O resultado deve ser semelhante à imagem abaixo:

    ![Mostrando os destinos de referência da câmera, agora definido.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Capítulo 10 – testar no editor do Unity

Teste se a configuração de cena está implementada corretamente.

Certifique-se de que:

-   Todos os scripts são anexados ao objeto da **câmera principal** . 
-   Todos os campos no *painel principal do Inspetor de câmera* são atribuídos corretamente.

1.  Pressione o botão **reproduzir** no *Editor do Unity*. O aplicativo deve estar em execução no headset de imersão anexado.

2.  Experimente alguns declarações, como:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Se você vir um erro no console do Unity sobre a alteração do dispositivo de áudio padrão, a cena poderá não funcionar conforme o esperado. Isso ocorre devido à maneira como o portal de realidade misturada lida com microfones internos para fones de ouvido que os têm. Se você vir esse erro, simplesmente pare a cena e inicie-a novamente e as coisas devem funcionar conforme o esperado.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Capítulo 11 – criar e sideloadr a solução UWP

Depois de garantir que o aplicativo está funcionando no editor do Unity, você estará pronto para compilar e implantar.

Para compilar:

1.  Salve a cena atual clicando em **arquivo > salvar**.
2.  Vá para **arquivo > configurações de Build**.
3.  Marque a caixa chamada **projetos C# do Unity** (útil para ver e depurar seu código assim que o projeto UWP for criado.
4.  Clique em **Adicionar e abrir cenas**e em **Compilar**.

    ![Janela de configurações de compilação](images/AzureLabs-Lab3-43.png)

4.  Você será solicitado a selecionar a pasta na qual deseja criar a solução. 

5.  Crie uma pasta *Builds* e dentro dessa pasta crie outra pasta com um nome apropriado de sua escolha. 
6.  Clique em **Selecionar pasta** para iniciar a compilação nesse local.
 
    ![criar a pasta builds](images/AzureLabs-Lab3-44.png)
    ![selecionar a pasta builds](images/AzureLabs-Lab3-45.png)
 
7.  Depois de concluir a compilação do Unity (pode levar algum tempo), ele deve abrir uma janela do **Explorador de arquivos** no local de sua compilação.

Para implantar no computador local:

1.  No *Visual Studio*, abra o arquivo de solução que foi criado no [capítulo anterior](#chapter-10--test-in-the-unity-editor).
2.  Na **plataforma da solução**, selecione **x86**, **computador local**.
3.  Na **configuração da solução** , selecione **depurar**.

    > Para o Microsoft HoloLens, você pode achar mais fácil definir isso como *computador remoto*, para que você não esteja vinculado ao seu computador. No entanto, também será necessário fazer o seguinte:
    > - Conheça o **endereço IP** do seu HoloLens, que pode ser encontrado dentro das *configurações > rede & Internet > Wi-Fi > opções avançadas*; o IPv4 é o endereço que você deve usar. 
    > - Verificar se o modo **de** **desenvolvedor** está ativado; encontrado em *configurações > atualização & > de segurança para desenvolvedores*.

    ![Implantar aplicativo](images/AzureLabs-Lab3-46.png)
 
4.  Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.
5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado!
6.  Depois de iniciado, o aplicativo solicitará que você autorize o acesso ao _microfone_. Use os *controladores de movimento*ou a *entrada de voz*ou o *teclado* para pressionar o botão **Sim** . 

## <a name="chapter-12--improving-your-luis-service"></a>Capítulo 12 – melhorando seu serviço LUIS

>[!IMPORTANT] 
> Este capítulo é incrivelmente importante e pode precisar ser iterado várias vezes, pois isso ajudará a melhorar a precisão do seu serviço LUIS: Certifique-se de concluir isso.

Para melhorar o nível de compreensão fornecido pelo LUIS, você precisa capturar novos declarações e usá-los para treinar novamente seu aplicativo LUIS.

Por exemplo, você pode ter treinado LUIS para entender "aumentar" e "upsizing", mas não iria querer que seu aplicativo também entenda palavras como "ampliar"?

Depois de usar seu aplicativo algumas vezes, tudo o que você disse será coletado pelo LUIS e disponível no PORTAL do LUIS.

1.  Acesse o aplicativo do portal seguindo este [link](https://www.luis.ai/home)e faça logon.
2.  Depois de fazer logon com suas credenciais do MS, clique no *nome do aplicativo*.
3.  Clique no botão **examinar ponto de extremidade declarações** à esquerda da página.

    ![Examinar declarações](images/AzureLabs-Lab3-47.png)
 
4.  Você verá uma lista dos declarações que foram enviados ao LUIS pelo seu aplicativo de realidade misturada.

    ![Lista de declarações](images/AzureLabs-Lab3-48.png)
 
Você observará algumas *entidades*realçadas. 

Ao focalizar cada palavra realçada, você pode examinar cada expressão e determinar qual entidade foi reconhecida corretamente, quais entidades estão erradas e quais entidades estão ausentes.

No exemplo acima, foi detectado que a palavra "Spear" foi realçada como um destino, portanto, é necessário corrigir o erro, o que é feito ao passar pela palavra com o mouse e clicar em **remover rótulo**.

![verificar declarações](images/AzureLabs-Lab3-49.png)
![remover imagem de rótulo](images/AzureLabs-Lab3-50.png)
 
5.  Se encontrar declarações que estejam completamente errados, você poderá excluí-los usando o botão **excluir** no lado direito da tela.

    ![Excluir declarações incorretos](images/AzureLabs-Lab3-51.png)

6.  Ou se sentir que o LUIS interpretou o expressão corretamente, você poderá validar sua compreensão usando o botão **Adicionar à intenção alinhada** .

    ![Adicionar à intenção alinhada](images/AzureLabs-Lab3-52.png)

7.  Depois de classificar todos os declarações exibidos, tente e recarregue a página para ver se há mais informações disponíveis.
8.  É muito importante repetir esse processo tantas vezes quanto possível para melhorar a compreensão do seu aplicativo. 

**Divertir-se!**

## <a name="your-finished-luis-integrated-application"></a>Seu aplicativo LUIS Integrated concluído

Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço do Azure Reconhecimento vocal Intelligence, para entender o que um usuário diz e agir sobre essas informações.

![Resultado do laboratório](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Ao usar esse aplicativo, você pode notar que, se olhar no objeto Floor e pedir para alterar sua cor, ele fará isso. Você pode solucionar como impedir que seu aplicativo altere a cor do piso?

### <a name="exercise-2"></a>Exercício 2

Tente estender os recursos de LUIS e de aplicativo, adicionando funcionalidades adicionais para objetos em cena; como exemplo, crie novos objetos no ponto de acesso olhar, dependendo do que o usuário diz e, em seguida, use esses objetos junto com os objetos de cena atuais, com os comandos existentes. 
