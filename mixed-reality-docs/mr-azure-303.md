---
title: MR e Azure 303 - (LUIS) de compreensão de idioma Natural
description: Conclua este curso para aprender a implementar o Azure Language Intelligence Service Luis (reconhecimento vocal) dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, serviço de inteligência de reconhecimento vocal, luis, hololens, vr de imersão,
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590557"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR e o Azure 303: Compreensão de idioma natural (LUIS)

Neste curso, você aprenderá como integrar a compreensão de idioma em um aplicativo de realidade misturada usando serviços Cognitivos do Azure, com a API de reconhecimento vocal.

![resultado de laboratório](images/AzureLabs-Lab3-000.png)

*Compreensão de idioma (LUIS)* é um serviço do Microsoft Azure, que fornece aos aplicativos com capacidade de fazer o significado fora de entrada do usuário, como por meio de extrair o que uma pessoa poderá, em suas próprias palavras. Isso é feito por meio do machine learning, que compreende e aprende as informações de entrada e, em seguida, pode responder com informações relevantes, detalhadas. Para obter mais informações, visite o [página do Azure (Luis reconhecimento vocal)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).

Com a conclusão deste curso, você terá um aplicativo de imersivo headset de realidade misturada que serão capaz de fazer o seguinte:

1.  Captura de fala de entrada de usuário, usando o microfone conectado para o fone de ouvido envolvente. 
2.  Enviar o ditado capturado a *serviço inteligente de reconhecimento de linguagem do Azure* (*LUIS*). 
3.  Ter extração de LUIS, que significa que a partir das informações de envio, que serão analisadas e tentam determinar que a intenção da solicitação do usuário será feita.

Desenvolvimento incluirá a criação de um aplicativo em que o usuário será capaz de usar voz e/ou olhar para alterar o tamanho e a cor dos objetos na cena. O uso de controladores de movimento não será abordado.

Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design. Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity. Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.

Esteja preparado para treinar LUIS várias vezes, que é abordado na [capítulo 12](#chapter-12--improving-your-luis-service). Você obterá melhores resultados os mais vezes que LUIS foi treinado.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>MR e o Azure 303: Compreensão de idioma natural (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens. Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens. Ao usar o HoloLens, você pode perceber algum eco durante a captura de voz.

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#. Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018). Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .

Recomendamos que o hardware e software para este curso a seguir:

- Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md)
- [O SDK mais recente do Windows 10](install-the-tools.md)
- [2017.4 do Unity](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado
- Um conjunto de fones de ouvido com um microfone interno (se o fone de ouvido não tiver um mic internos e alto-falantes)
- Acesso à Internet para a instalação do Azure e a recuperação do LUIS

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação). 
2.  Para permitir que seu computador habilitar o ditado, vá para **configurações do Windows > privacidade > fala, escrita à tinta e digitando** e pressione o botão **ativar serviços de fala e sugestões de digitação**.
3.  O código neste tutorial permitirá que você deseja gravar dos **dispositivo padrão de microfone** definido em seu computador. Verifique se que o dispositivo de microfone padrão está definido como aquele que você deseja usar para capturar sua voz.
4.  Se o fone de ouvido tem um microfone interno, certifique-se a opção *"Quando eu wear meu fone de ouvido, alternar para o fone de ouvido mic"* está ativado na *Portal de realidade misturada* configurações.

    ![Configurando o fone de ouvido envolvente](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Capítulo 1 – configurar o Portal do Azure

Para usar o *vocal* serviço no Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.

1.  Faça logon na [Portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

2.  Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure *vocal*e clique em **Enter**. 

    ![Criar recurso do LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.
 
3.  A nova página à direita fornece uma descrição do serviço de reconhecimento vocal. Na parte inferior esquerda desta página, selecione a **criar** botão para criar uma instância desse serviço.

    ![Criação do serviço LUIS - aviso legal](images/AzureLabs-Lab3-02.png)
 
4.  Depois de clicar em criar:

    1. Inserir sua desejada **nome** para esta instância de serviço.
    2. Selecione uma **assinatura**.
    3. Selecione o **tipo de preço** apropriado para você, se esse for o primeiro tempo para criar um *Service LUIS*, uma camada gratuita (chamada F0) deve estar disponível para você. A alocação livre deve ser mais do que suficiente para este curso.
    4. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local seria o ideal é que na região em que o aplicativo é executado. Alguns ativos do Azure estão disponíveis somente em determinadas regiões.
    6. Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.
    7. Selecione **Criar**.

        ![Criar serviço LUIS - entrada do usuário](images/AzureLabs-Lab3-03.png)
 
5.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.
6.  Uma notificação será exibida no portal depois que a instância do serviço é criada. 
 
    ![Nova imagem de notificação do Azure](images/AzureLabs-Lab3-04.png)

7.  Clique na notificação para explorar a nova instância do serviço.

    ![Notificação de criação do recurso com êxito](images/AzureLabs-Lab3-05.png)
 
8.  Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço. Você será levado para a nova instância do serviço LUIS. 
 
    ![Acessando chaves LUIS](images/AzureLabs-Lab3-06.png)

9.  Dentro deste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, que é feito por meio do uso de chave de assinatura do seu serviço.
10. Dos *início rápido* página, de seu *API LUIS* do serviço, navegue até a primeira etapa, *pegue suas chaves*e clique em **chaves** (você também pode fazer isso clicando no hiperlink azul chaves, localizado no menu de navegação de serviços, indicado pelo ícone de chave). Isso irá revelar o seu serviço *chaves*.
11. Faça uma cópia de uma das chaves exibidas, pois precisará dele posteriormente em seu projeto. 
12. No *Service* , clique em *Portal do reconhecimento vocal* ser redirecionado para a página da Web que você usará para criar seu novo serviço no App LUIS. 

## <a name="chapter-2--the-language-understanding-portal"></a>Capítulo 2 – o Portal do reconhecimento vocal

Nesta seção, você aprenderá como fazer um App LUIS no Portal do LUIS. 

> [!IMPORTANT]
> Por favor, lembre-se que a configuração de *entidades*, *intenções*, e *declarações* dentro deste capítulo é apenas a primeira etapa na criação de seu serviço LUIS: você também precisará treinar novamente o serviço, várias vezes, portanto, para torná-lo mais precisos. Treinar novamente seu serviço é abordado a [último capítulo](#chapter-12--improving-your-luis-service) deste curso, portanto, certifique-se de que você conclua.

1.  Ao atingir o *Portal do reconhecimento vocal*, talvez seja necessário fazer logon, se você não ainda estiver, com as mesmas credenciais que o seu portal do Azure. 

    ![Página de logon do LUIS](images/AzureLabs-Lab3-07.png)
 
2.  Se essa for sua primeira vez usando o LUIS, você precisará rolar para baixo até a parte inferior da página de boas-vinda, para localizar e clique no **aplicativo LUIS criar** botão.

    ![Criar página de aplicativo LUIS](images/AzureLabs-Lab3-08.png)
 
3.  Depois de conectado, clique em **meus aplicativos** (se você não estiver nessa seção). Você pode, em seguida, clique em **criar novo aplicativo**.

    ![LUIS - minha imagem de aplicativos](images/AzureLabs-Lab3-09.png)
 
4.  Dar ao seu aplicativo uma *nome*.
5.  Se seu aplicativo deve para compreender um idioma diferente do inglês, você deve alterar o *cultura* para o idioma apropriado.
6.  Aqui você também pode adicionar um *descrição* do seu novo aplicativo LUIS.

    ![LUIS - criar um novo aplicativo](images/AzureLabs-Lab3-10.png)

7.  Depois de pressionar **feito**, você inserirá o *compilar* página de seu novo *LUIS* aplicativo.
8.  Há alguns conceitos importantes para entender aqui:

    -   *Intenção*, representa o método que será chamado após uma consulta do usuário. Uma *INTENÇÃO* pode ter um ou mais *ENTIDADES*.
    -   *Entidade*, é um componente da consulta que descreve informações relevantes para o *INTENÇÃO*.
    -   *Declarações*, são exemplos de consultas fornecido pelo desenvolvedor, que LUIS usará para treinar a próprio.

Se esses conceitos não são perfeitamente desmarcar, não se preocupe, pois este curso esclarecê-los ainda mais neste capítulo.

Você começará criando os *entidades* necessários para compilar este curso.

9.  No lado esquerdo da página, clique em *entidades*, em seguida, clique em **criar nova entidade**.

    ![Criar nova entidade](images/AzureLabs-Lab3-11.png)

10. Chame a nova entidade *cor*, defina seu tipo como *simples*, em seguida, pressione **feito**.

    ![Criar entidade simples - cor](images/AzureLabs-Lab3-12.png)
 
11. Repita esse processo para criar três (3) mais entidades simples chamado:

    -   *upsize*
    -   *downsize*
    -   *target*

O resultado deve ser semelhante a imagem a seguir:

![Resultado da criação da entidade](images/AzureLabs-Lab3-13.png)
 
Agora você pode começar a criar *intenções*. 

> [!WARNING]
> Não exclua os **None** intenção.

12. No lado esquerdo da página, clique em **intenções**, em seguida, clique em **criar novo propósito**.

    ![Criar novas tentativas](images/AzureLabs-Lab3-14.png)

13. Chame o novo *intenção* **ChangeObjectColor**.

    > [!IMPORTANT]
    > Isso *intenção* nome é usado dentro do código posteriormente no curso, portanto, para obter melhores resultados, use esse nome exatamente como fornecido.

Depois que você confirme o nome que você será direcionado para a página de tentativas.

![LUIS - página intenções](images/AzureLabs-Lab3-15.png)

Você observará que há uma caixa de texto solicitando que você para o tipo de 5 ou mais diferente *declarações*.

> [!NOTE]
> LUIS converte todas as declarações em letras minúsculas.

14. Insira o seguinte *expressão* na caixa de texto superior (atualmente com o texto *digite exemplos cerca de 5...* ) e pressione **Enter**:

```
The color of the cylinder must be red
```

Você observará que o novo *expressão* aparecerá em uma lista abaixo.

Seguindo o mesmo processo, insira as seguintes declarações de seis (6):

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Para cada expressão que você criou, você deve identificar quais palavras devem ser usadas pelo LUIS como entidades. Neste exemplo, você precisa rotular todas as cores como uma *cor* entidade e todos os possíveis referência a um destino como um *destino* entidade.

15. Para fazer isso, tente clicar na palavra *cilindro* na primeira expressão e selecione *destino*.

    ![Identificar alvos de expressão](images/AzureLabs-Lab3-16.png)
 
16. Agora, clique na palavra *vermelho* na primeira expressão e selecione *cor*.

    ![Identificar as entidades de expressão](images/AzureLabs-Lab3-17.png)
 
17. Além disso, a próxima linha do rótulo em que *cubo* deve ser um *destino*, e *preto* deve ser um *cor*. Observe também o uso de palavras *'this'*, *'it'*, e *'este objeto'*, que estamos fornecendo, portanto, ter tipos de destino não específicas disponíveis também. 

18. Repita o processo acima até que todas as declarações têm as entidades rotuladas. Consulte a imagem se você precisar de ajuda abaixo.

    > [!TIP]
    > Ao selecionar palavras para rotulá-los como entidades:
    > - Para palavras individuais, basta clicá-los.
    > - Para um conjunto de duas ou mais palavras, clique no início e no final do conjunto.

    > [!NOTE]
    > Você pode usar o *modo de exibição de Tokens* botão Ativar/desativar para alternar entre **entidades / Tokens exibir**!

19. Os resultados devem ser, conforme mostrado nas imagens a seguir, mostrando os **entidades / Tokens exibir**:

    ![Tokens e modos de exibição de entidades](images/AzureLabs-Lab3-18.png)
  
20. Agora pressione a **Train** botão no canto superior direito da página e aguarde até o pequeno indicador de round-la para ficar verde. Isso indica que LUIS foi treinado com êxito para reconhecer a intenção.

    ![Treinar LUIS](images/AzureLabs-Lab3-19.png)
 
21. Como um exercício para você, crie um novo propósito chamado **ChangeObjectSize**, usando as entidades *destino*, *upsizing*, e *diminuir o tamanho de*.
22. Seguindo o mesmo processo que a intenção anterior, insira as seguintes oito (8) declarações para *tamanho* alterar:

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

23. O resultado deve ser como o mostrado na imagem abaixo:

    ![Configurar Tokens ChangeObjectSize / entidades](images/AzureLabs-Lab3-20.png) 

24. Uma vez ambas as intenções **ChangeObjectColor** e **ChangeObjectSize**, foram criados e treinado, clique no **publicar** botão na parte superior da página.

    ![Publicar o serviço LUIS](images/AzureLabs-Lab3-21.png)

25. Sobre o *publicar* página você finalizar e publicar seu App LUIS para que ele possa ser acessado pelo seu código.

    1. Defina a operação de soltar para baixo *Publish To* como **produção**.
    2. Defina as *fuso horário* para seu fuso horário.
    3. A caixa de seleção **prevista de incluir todas as pontuações de intenção**.
    4. Clique em **publicar no Slot de produção**.

        ![Configurações de publicação](images/AzureLabs-Lab3-22.png)

26. Na seção *recursos e as chaves*:

    1.  Selecione a região que você definiu para a instância de serviço no Portal do Azure.
    2.  Você observará uma **Starter_Key** elemento abaixo, ignorá-la.
    3.  Clique em **Add Key** e insira o *chave* que você obteve no Portal do Azure quando você criou sua instância de serviço. Se o Azure e o portal de LUIS estiver conectados ao mesmo usuário, você receberá menus suspensos para *nome do locatário*, *nome da assinatura*e o *chave* você deseja usar ( terá o mesmo nome que você forneceu anteriormente no Portal do Azure.

    > [!IMPORTANT] 
    > Sob *ponto de extremidade*, faça uma cópia do ponto de extremidade correspondente à chave inserida por você, você irá usá-lo em breve em seu código.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Capítulo 3 – configurar o projeto do Unity

A seguir é um conjunto típico backup para o desenvolvimento com a realidade misturada e como tal, é um bom modelo para outros projetos.

1.  Abra *Unity* e clique em **New**. 

    ![Inicie um novo projeto do Unity.](images/AzureLabs-Lab3-24.png)

2.  Agora você precisará fornecer um nome de projeto do Unity, insira **MR_LUIS**. Verifique se o tipo de projeto é definido como **3D**. Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab3-25.png)
 
3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Acesse Editar > Preferências e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![Atualize as preferências do editor de script.](images/AzureLabs-Lab3-26.png)
 
4.  Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma** botão.

    ![Crie janela de configurações, alternar a plataforma para a UWP.](images/AzureLabs-Lab3-27.png)
 
5.  Vá para **arquivo > configurações de Build** e certifique-se de que:

    1. **Dispositivo de destino** é definido como **qualquer dispositivo**

        > Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.

    2. **Tipo de compilação** é definido como **D3D**
    3. **SDK** é definido como **mais recente instalada**
    4. **Versão do Visual Studio** é definido como **mais recente instalada**
    5. **Compilar e executar** é definido como **Máquina Local**
    6. Salve a cena e adicioná-lo para a compilação.

        1. Fazer isso selecionando **cenas abra Adicionar**. Salvamento janela será exibida.
        
            ![Clique em Adicionar botão cenas aberto](images/AzureLabs-Lab3-28.png)

        2. Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.

            ![Criar nova pasta de scripts](images/AzureLabs-Lab3-29.png)

        3. Abra seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo*: campo de texto, digite **MR_LuisScene**, em seguida, pressione **salvar**.

            ![Dê um nome de nova cena.](images/AzureLabs-Lab3-30.png)

    7. O restante de configurações, em *configurações de Build*, deverá ser deixado como padrão por enquanto.

6. No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado. 

    ![Abra configurações do player.](images/AzureLabs-Lab3-31.png) 
 
7. Neste painel, algumas configurações precisam ser verificados:

    1. No **outras configurações** guia:

        1. **Versão de tempo de execução de scripts** deve ser **estável** (.NET 3.5 equivalente).
        2. **Script de back-end** deve ser **.NET**
        3. **Nível de compatibilidade de API** deve ser **.NET 4.6**

            ![Outras configurações de atualização.](images/AzureLabs-Lab3-32.png)
      
    2. Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        1. **InternetClient**
        2. **Microfone**

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab3-33.png)

    3. Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.

        ![Atualize as configurações de R de X.](images/AzureLabs-Lab3-34.png)

8.  Volta *configurações de Build* _Unity C#_  projetos não fica acinzentado; marque a caixa de seleção ao lado disso. 
9.  Feche a janela de configurações de Build.
10. Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).

## <a name="chapter-4--create-the-scene"></a>Capítulo 4-criar a cena

> [!IMPORTANT]
> Se você quiser ignorar a *configurar o Unity* componente deste curso e continuar diretamente no código, fique à vontade para baixá-lo [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importá-lo para seu projeto como um [pacote personalizado ](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 5](#chapter-5--create-the-microphonemanager-class). 

1.  Clique com botão direito em uma área vazia do *painel de hierarquia*, em **objeto 3D**, adicionar um **plano**.

    ![Crie um plano.](images/AzureLabs-Lab3-35.png)

2.  Lembre-se que quando você clique com botão direito dentro de *hierarquia* novamente para criar mais objetos, se você ainda tiver o último objeto selecionado, o objeto selecionado será o pai do seu novo objeto. Evite isso left-clicking em um espaço vazio dentro da hierarquia e, em seguida, clicando duas vezes.

3.  Repita o procedimento acima para adicionar os seguintes objetos:

    1. *Sphere*
    2. *Cilindro*
    3. *Cube*
    4. *3D Text*

4.  A cena resultante *hierarquia* deve ser como o mostrado na imagem abaixo:

    ![Configuração da hierarquia de cena.](images/AzureLabs-Lab3-36.png)
 
5.  Clique com o botão esquerdo na **câmera principal** para selecioná-la, examine o *painel Inspetor* você verá o objeto de câmera com todas as a seus componentes.
6.  Clique no **Add Component** botão localizado na parte inferior do *painel Inspetor*.

    ![Adicionar fonte de áudio](images/AzureLabs-Lab3-37.png)
 
7.  Pesquise o componente chamado *Audio Source*, conforme mostrado acima.
8.  Também verifique se o *transformar* componente da câmera principal é definido como (0, 0,0), isso pode ser feito, pressionando as **engrenagem** ícone ao lado da câmera *transformar* componente e selecionando **redefinir**. O *transformar* componente, em seguida, deve se parecer com:

    1.  *Posição* é definido como **0, 0, 0**.
    2.  *Rotação* é definido como **0, 0, 0**.

    > [!NOTE] 
    > Para o Microsoft HoloLens, você precisará alterar também o seguinte, que fazem parte dos **câmera** componente, que está no seu **câmera principal**:
    > - **Limpe os sinalizadores de:** Cor sólida.
    > - **Plano de fundo** ' preto, alfa 0' – cor hexadecimal: 00000000 #.

9.  Clique com o botão esquerdo na **plano** para selecioná-lo. No *painel Inspetor* definir os *transformar* componente com os seguintes valores:

    |       | Transformar - *posição* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 0     | -1                     | 0     |


10. Clique com o botão esquerdo na **esfera** para selecioná-lo. No *painel Inspetor* definir os *transformar* componente com os seguintes valores:

    |       | Transformar - *posição* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 2     | 1                      | 2     |

11. Clique com o botão esquerdo na **cilindro** para selecioná-lo. No *painel Inspetor* definir os *transformar* componente com os seguintes valores:

    |       | Transformar - *posição* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | -2    | 1                      | 2     |

12. Clique com o botão esquerdo na **cubo** para selecioná-lo. No *painel Inspetor* definir os *transformar* componente com os seguintes valores:

    |        | Transformar - *posição* |       |  \| |       | Transformar - *rotação* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Clique com o botão esquerdo na **novo texto** objeto para selecioná-lo. No *painel Inspetor* definir os *transformar* componente com os seguintes valores:

    |       | Transformar - *posição* |       |  \| |       | Transformar - *escala* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. Alteração **Font Size** na **texto de malha** componente **50**.
15. Alterar o *nome* da **texto de malha** o objeto para a **texto ditado**.

    ![Criar objeto de texto 3D](images/AzureLabs-Lab3-38.png)
 
16. A estrutura de hierarquia painel agora deve ser assim:

    ![texto de malha no modo de exibição de cena](images/AzureLabs-Lab3-38b.png)


17. A cena final deve parecer com a imagem a seguir:

    ![O modo de exibição de cena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Capítulo 5 – criar a classe MicrophoneManager

É o primeiro Script que você pretende criar o *MicrophoneManager* classe. Depois disso, você aprenderá a criar o *LuisManager*, o *comportamentos* classe e por fim, o *olhares* classe (fique à vontade para criar todos esses agora, embora será abordada como você alcance cada capítulo).

O *MicrophoneManager* classe é responsável por:

-   Detectando o dispositivo de gravação anexado ao computador (o que é o padrão) ou fone de ouvido.
-   Capturar áudio (voz) e usar ditado para armazená-la como uma cadeia de caracteres.
-   Depois que a voz foi pausado, enviar o ditado para o *LuisManager* classe. 

Para criar essa classe: 

1.  Clique com botão direito no *painel do projeto*, **criar > pasta**. Chame a pasta **Scripts**. 

    ![Crie a pasta de Scripts.](images/AzureLabs-Lab3-40.png)
 
2.  Com o **Scripts** pasta criada, clique duas vezes nele para abrir. Em seguida, dentro dessa pasta, direito do mouse **criar > C# Script**. Nomeie o script *MicrophoneManager*. 

3.  Clique duas vezes em *MicrophoneManager* para abri-lo com *Visual Studio*.
4.  Adicione os namespaces a seguir na parte superior do arquivo:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro do *MicrophoneManager* classe:

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado. Eles serão chamados quando inicializa a classe:

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
 
7.  Agora, você precisa que o método que o aplicativo usa para iniciar e parar a captura de voz e passá-lo para o *LuisManager* classe, que você criará em breve. 

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

8.  Adicionar um *ditado manipulador* que será invocado quando a voz pausa. Esse método irá passar o texto ditado para o *LuisManager* classe.

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
    > Excluir o *Update ()* método uma vez que essa classe não irá usá-lo.

9.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

    > [!NOTE]
    > Neste ponto, você observará um erro que aparecem na *painel de Console do Editor do Unity*. Isso ocorre porque o código faz referência a *LuisManager* classe que você criará no próximo capítulo.

## <a name="chapter-6--create-the-luismanager-class"></a>Capítulo 6 – criar a classe LUISManager

É hora de criar o *LuisManager* classe, que faz com que a chamada para o serviço LUIS do Azure. 

A finalidade dessa classe é receber o texto ditado do *MicrophoneManager* classe e enviá-lo para o *API de reconhecimento vocal Azure* a serem analisados.

Essa classe desserializará o *JSON* resposta e chamar os métodos apropriados da *comportamentos* classe para disparar uma ação.

Para criar essa classe: 

1.  Clique duas vezes no **Scripts** pasta para abri-lo. 
2.  Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**. Nomeie o script *LuisManager*. 
3.  Clique duas vezes no script para abri-lo com o Visual Studio.
4.  Adicione os namespaces a seguir na parte superior do arquivo:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Você começará criando três classes **dentro de** as *LuisManager* classe (dentro do mesmo arquivo de script, acima o *Start ()* método) que representará o desserializado Resposta JSON do Azure.

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

6.  Em seguida, adicione as seguintes variáveis dentro do *LuisManager* classe:
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Certifique-se de colocar o ponto de extremidade do LUIS no agora (que você terá de seu portal LUIS).

8.  Código para o *Awake()* método agora precisa ser adicionado. Esse método será chamado quando a classe é inicializado:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  Agora, você precisa que os métodos que esse aplicativo usa para enviar o ditado recebido do *MicrophoneManager* classe *LUIS*e, em seguida, receber e desserializar a resposta. 
10. Depois de determinar o valor da intenção e as entidades associadas, eles são passados para a instância das *comportamentos* classe para disparar a ação pretendida.

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
 
11. Criar um novo método chamado *AnalyseResponseElements()* lerá resultante *AnalysedQuery* e determinar as entidades. Depois que essas entidades são determinadas, eles serão passados para a instância das *comportamentos* classe a ser usada nas ações.

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

            // Depending on the topmost recognised intent, read the entities name
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
    > Excluir o *Start ()* e *Update ()* métodos, já que essa classe não irá usá-los.

12. Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

> [!NOTE]
> Neste ponto, você vai notar vários erros que aparecem na *painel de Console do Editor do Unity*. Isso ocorre porque o código faz referência a *comportamentos* classe que você criará no próximo capítulo.

## <a name="chapter-7--create-the-behaviours-class"></a>Capítulo 7 – criar a classe de comportamentos

O *comportamentos* classe irá disparar as ações usando as entidades fornecidas pelo *LuisManager* classe.

Para criar essa classe: 

1.  Clique duas vezes no **Scripts** pasta para abri-lo. 
2.  Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**. Nomeie o script *comportamentos*. 
3.  Clique duas vezes para abri-lo com o script *Visual Studio*.
4.  Em seguida, adicione as seguintes variáveis dentro do *comportamentos* classe:

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Adicione a *Awake()* código do método. Esse método será chamado quando a classe é inicializado:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  Os seguintes métodos são chamados pelo *LuisManager* classe (que você criou anteriormente) para determinar qual objeto é o destino da consulta e, em seguida, disparar a ação apropriada.

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
 
7.  Adicione a *FindTarget()* método para determinar quais as *GameObjects* é o destino da intenção atual. Este método assume como padrão o destino para o *GameObject* sendo "gazed" se nenhum destino explícito é definido nas entidades.

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
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
    > Excluir o *Start ()* e *Update ()* métodos, já que essa classe não irá usá-los.

8.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-8--create-the-gaze-class"></a>Capítulo 8 – criar a classe de olhar

A última classe que você precisará concluir este aplicativo é o *olhares* classe. Essa classe atualiza a referência para o *GameObject* em foco de visual do usuário no momento.

Para criar essa classe: 

1.  Clique duas vezes no **Scripts** pasta para abri-lo. 
2.  Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**. Nomeie o script *olhares*. 
3.  Clique duas vezes para abri-lo com o script *Visual Studio*.
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

## <a name="chapter-9--completing-the-scene-setup"></a>Capítulo 9 – concluir a configuração de cena

1.  Para concluir a instalação da cena, arraste cada script que você tenha criado a partir da pasta de Scripts para o **câmera principal** do objeto na *painel de hierarquia*.
2.  Selecione o **câmera principal** e examine o *painel Inspetor*, você deve ser capaz de ver cada script que você já anexou e você observará que há parâmetros em cada script que ainda estão a ser definido.

    ![Definindo os destinos de referência de câmera.](images/AzureLabs-Lab3-41.png)

3.  Para definir esses parâmetros corretamente, siga estas instruções:

    1. *MicrophoneManager*:

        - Do *painel de hierarquia*, arraste o **texto ditado** objeto para o **texto ditado** caixa do valor de parâmetro.

    2. *Comportamentos*, do *painel de hierarquia*:

        - Arraste o **esfera** do objeto para o *esfera* caixa do destino de referência.
        - Arraste o **cilindro** para o *cilindro* caixa do destino de referência.
        - Arraste o **cubo** para o *cubo* caixa do destino de referência.

    3. *Gaze*:

        - Defina as *olhares Max distância* para **300** (se ele não ainda estiver). 

4.  O resultado deve ser semelhante a imagem a seguir:

    ![Agora, mostrando os destinos de referência de câmera, defina.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Capítulo 10 – teste no Editor do Unity

Teste a configuração de cena é implementada corretamente.

Certifique-se de que:

-   Todos os scripts são anexados para o **câmera principal** objeto. 
-   Todos os campos a *painel de Inspetor de câmera principal* são atribuídas corretamente.

1.  Pressione a **reproduzir** botão na *Editor do Unity*. O aplicativo deve estar executando dentro de fone de ouvido imersivo anexado.

2.  Tente algumas frases, tais como:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Se você vir um erro no console do Unity sobre o dispositivo de áudio padrão a alteração, a cena pode não funcionar conforme o esperado. Isso é devido à maneira como o portal de realidade misturada lida com microfones internos para fones de ouvido que têm-los. Se você vir esse erro, simplesmente parar a cena e iniciá-lo novamente e as coisas devem funcionar como esperado.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Capítulo 11 – Build e carregar a solução de UWP

Depois que você garante que o aplicativo está funcionando no Editor do Unity, você está pronto para compilar e implantar.

Para construir:

1.  Salve a cena atual clicando em **arquivo > Salvar**.
2.  Vá para **arquivo > configurações de Build**.
3.  Marque a caixa denominada **Unity C# projetos** (útil para ver e depurar seu código depois de criar o projeto UWP.
4.  Clique em **adicionar cenas aberto**, em seguida, clique em **Build**.

    ![Janela de configurações da compilação](images/AzureLabs-Lab3-43.png)

4.  Você será solicitado a selecionar a pasta onde você deseja criar a solução. 

5.  Criar uma *compilações* pasta e dentro dessa pasta, crie outra pasta com um nome apropriado de sua escolha. 
6.  Clique em **Selecionar pasta** para iniciar a compilação nesse local.
 
    ![Criar pasta Builds](images/AzureLabs-Lab3-44.png)
    ![Select cria a pasta](images/AzureLabs-Lab3-45.png)
 
7.  Uma vez Unity terminou de construção (pode levar algum tempo), ele deverá abrir um **Explorador de arquivos** janela no local de sua compilação.

Para implantar no computador Local:

1.  Na *Visual Studio*, abra o arquivo de solução que foi criado na [capítulo anterior](#chapter-10--test-in-the-unity-editor).
2.  No **plataforma da solução**, selecione **x86**, **Máquina Local**.
3.  No **configuração da solução** selecionar **depurar**.

    > Para o Microsoft HoloLens, talvez você ache mais fácil de definir isso como *máquina remota*, de modo que você não estiver vinculado ao seu computador. No entanto, você precisará também fazer o seguinte:
    > - Saber a **endereço IP** de seu HoloLens, que podem ser encontrado dentro a *Configurações > rede e Internet > Wi-Fi > Opções avançadas de*; o IPv4 é o endereço que você deve usar. 
    > - Certifique-se **modo de desenvolvedor** é **na**; encontrado na *Configurações > atualização e segurança > para os desenvolvedores*.

    ![Implantar aplicativo](images/AzureLabs-Lab3-46.png)
 
4.  Vá para o **menu Build** e clique em **implantar solução** para carregar o aplicativo em seu computador.
5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado!
6.  Depois de iniciado, o aplicativo solicitará que você autorizar o acesso para o _microfone_. Use o *controladores movimento*, ou *entrada de voz*, ou o *teclado* pressionar o **Sim** botão. 

## <a name="chapter-12--improving-your-luis-service"></a>Capítulo 12 – melhorando o seu serviço LUIS

>[!IMPORTANT] 
> Este capítulo é incrivelmente importante e talvez precise ser interated após várias vezes, pois ajudará a melhorar a precisão do seu serviço LUIS: Certifique-se de concluir isso.

Para aumentar o nível de compreensão fornecida pelo LUIS, você precisa capturar novas declarações e usá-los para treinar novamente seu App LUIS.

Por exemplo, você pode ter treinado LUIS para entender a "Increase" e "Ampliar", mas não seria você quiser que seu aplicativo para também reconhecer palavras como "Ampliar"?

Depois que você usou seu aplicativo algumas vezes, tudo o que você já disse serão coletados pelo LUIS e estarão disponíveis no PORTAL do LUIS.

1.  Vá para seu aplicativo de portal seguindo este [LINK](https://www.luis.ai/home)e fazer logon.
2.  Depois que você está conectado com suas Credentials MS, clique em seu *nome do aplicativo*.
3.  Clique o **examine as declarações de ponto de extremidade** botão à esquerda da página.

    ![Examinar declarações](images/AzureLabs-Lab3-47.png)
 
4.  Você verá uma lista das declarações que foram enviadas para o LUIS pelo seu aplicativo de realidade misturada.

    ![Lista de declarações](images/AzureLabs-Lab3-48.png)
 
Você observará algumas realçado *entidades*. 

Passando o mouse sobre cada palavra realçada, você pode examinar cada expressão e determinar quais entidades foi reconhecida corretamente, quais entidades estão erradas e quais entidades são perdidas.

No exemplo acima, ele foi encontrado que a palavra "spear" tinha sido realçada como um destino, então ele necessárias para corrigir o erro, o que é feito ao passar o mouse sobre a palavra com o mouse e clicando em **remover rótulo**.

![Verificar as declarações](images/AzureLabs-Lab3-49.png)
![remover a imagem do rótulo](images/AzureLabs-Lab3-50.png)
 
5.  Se você encontrar declarações que estão completamente erradas, você poderá excluí-los usando o **excluir** botão no lado direito da tela.

    ![Excluir declarações erradas](images/AzureLabs-Lab3-51.png)

6.  Ou se você achar que LUIS tem a declaração interpretada corretamente, você pode validar sua compreensão usando o **adicionar a intenção alinhado** botão.

    ![Adicionar a intenção alinhada](images/AzureLabs-Lab3-52.png)

7.  Depois que você tenha classificado Rotulasse exibido, experimente e recarregue a página para ver se mais estão disponíveis.
8.  É muito importante repetir esse processo tantas vezes quanto possível melhorar seu entendimento do aplicativo. 

**Divertir-se!**

## <a name="your-finished-luis-integrated-application"></a>Seu aplicativo LUIS integrado concluído

Parabéns, você criou um aplicativo de realidade mista que aproveita o Azure serviço reconhecimento vocal inteligência, para entender o que um usuário diz e agir sobre essas informações.

![resultado de laboratório](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Ao usar este aplicativo, você pode observar que se você olhar no objeto do chão e pedir para alterar sua cor, ele fará isso. Você pode trabalhar como interromper a alterar a cor base do aplicativo?

### <a name="exercise-2"></a>Exercício 2

Experimente a extensão dos recursos de aplicativo e LUIS, acrescentando funcionalidade adicional para objetos na cena; Por exemplo, crie novos objetos ao olhar ponto de clique, dependendo do que o usuário diz e, em seguida, ser capaz de usá-los junto com objetos de cena atual, com os comandos existentes. 
