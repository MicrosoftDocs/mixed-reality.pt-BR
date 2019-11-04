---
title: Tutoriais de funcionalidades de vários usuários-2. Obtendo o Unity pronto para desenvolvimento
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 5d8194e9a51bdb0ce32f345b4adfbfaf408c5396
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438385"
---
# <a name="2-getting-unity-ready-for-development"></a>2. obtendo o Unity pronto para desenvolvimento 


Neste tutorial, você aprenderá a preparar e configurar o Unity para o desenvolvimento de aplicativos, incluindo a importação do kit de ferramentas de realidade mista, a definição de configurações de compilação e a preparação de sua cena.

## <a name="objectives"></a>Objetivos

- Configurar o Unity para o desenvolvimento de aplicativos

- Importe o Kit de ferramentas de realidade misturada

- Preparar a cena do projeto

## <a name="instructions"></a>Instruções

1. Baixe e salve o pacote da Unity do kit de ferramentas da realidade mista clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)

2. No Unity, clique no menu ativos e selecione Importar pacote e, em seguida, clique em pacote personalizado.

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Selecione o pacote do Unity que você acabou de baixar do link fornecido na etapa 1. Depois que a janela pop-up importar aparecer no Unity, clique no botão importar para começar a importar o MRTK. Isso pode levar vários minutos.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> Observação: o pacote baixado está em sua pasta local, em que você salvou o arquivo. A imagem acima não retrata onde você encontrará o pacote.

4. Crie uma nova cena. Isso pode ser feito clicando em arquivo e selecionando nova cena ". Salve-o como HLSharedProjectMain.

> Observação: você pode receber um pop-up parecido com a imagem abaixo. Por enquanto, clique em não.
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. Em kit de ferramentas de realidade mista, clique em Adicionar à cena e configurar.

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Quando isso for concluído, um novo arquivo de configuração será exibido, dando a você a opção de personalizar o perfil. Clique em copiar e personalizar.

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. Role para baixo e desmarque Habilitar o sistema de diagnóstico se desejar ocultar a janela de diagnóstico. É recomendável manter a janela de diagnóstico habilitada durante o desenvolvimento do aplicativo para monitorar o desempenho e, em seguida, desabilitá-lo durante as demonstrações de produção ou de aplicativo. 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Abra as configurações de Build pressionando Control + Shift + B ou indo para arquivo-> configurações de Build. Observe que o programa está definido atualmente na plataforma autônoma de PC, Mac e Linux. Para o desenvolvimento do HoloLens 2, defina a plataforma como Plataforma Universal do Windows. Selecione-o e clique em alternar plataforma.

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. Após a conclusão, clique na caixa chamada Add Open bastidores. Agora, acesse o painel Inspetor e verifique se a caixa de seleção à direita da realidade virtual com suporte (conforme mostrado na imagem abaixo) está marcada. Verifique também se a caixa de seleção ao lado de cenas/HLSharedProjectMain também está marcada, conforme mostrado na imagem abaixo.

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. Na seção Configurações de publicação no painel Inspetor, role para baixo até recursos e verifique se as seguintes caixas de seleção estão marcadas:

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. Importe o pacote personalizado chamado SharingAssetCollection, que pode ser baixado [aqui.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. No painel projeto, vá para a pasta pré-fabricados. Nas etapas a seguir, você implementará algumas pré-fabricados na cena. Na pasta pré-fabricados, clique e arraste a janela pré-fabricado, depurar para a hierarquia. Quando terminar, salve o projeto clicando em arquivo e, em seguida, salve ou pressione Control + S.

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > Observação: você pode notar que um pop-up aparece ao clicar no pré-fabricado, solicitando-lhe informações sobre o TMP Essentials. Clique em importar o TMP Essentials conforme necessário. Se essa janela pop-up for exibida, talvez seja necessário excluir o pré-fabricado de sua hierarquia e arrastá-lo novamente para a hierarquia para evitar possíveis erros relacionados a texto.
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Parabéns

Seu projeto de Unity agora está pronto para Photon. Nos próximos tutoriais, vamos criar essa cena e nosso projeto de Unity em direção a uma experiência compartilhada completa.

[Próximo tutorial: 3. conectando vários usuários](mrlearning-sharing(photon)-ch3.md)

