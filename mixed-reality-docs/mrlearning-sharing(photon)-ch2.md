---
title: Tutoriais de funcionalidades de vários usuários-2. Obtendo o Unity pronto para desenvolvimento
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 2bcec7e70949186c6e711120c36ee8649c006ec7
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553824"
---
# <a name="2-getting-unity-ready-for-development"></a>2. obtendo o Unity pronto para desenvolvimento

Neste tutorial, você aprenderá a preparar e configurar o Unity para o desenvolvimento de aplicativos, incluindo a importação do kit de ferramentas de realidade mista, a definição de configurações de compilação e a preparação de sua cena.

## <a name="objectives"></a>Objetivos

* Configurar o Unity para o desenvolvimento de aplicativos
* Importe o Kit de ferramentas de realidade misturada
* Preparar a cena do projeto

## <a name="instructions"></a>Instructions

1. Baixe e salve o pacote do kit de ferramentas da realidade do infigurador do Foundationity, clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

2. No Unity, clique no menu ativos e selecione Importar pacote e, em seguida, clique em pacote personalizado.

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Selecione o pacote do Unity que você acabou de baixar do link fornecido na etapa 1. Depois que a janela pop-up importar aparecer no Unity, clique no botão importar para começar a importar o MRTK. Isso pode levar vários minutos.

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >O pacote baixado está em sua pasta local, em que você salvou o arquivo. A imagem acima não retrata onde você encontrará o pacote.

    Depois que o pacote tiver sido importado, a janela Configurador de Projeto do MRTK deverá aparecer. Se não estiver, abra-o selecionando o kit de ferramentas do reality Toolkit > Utilities > configurar o projeto do Unity no menu do Unity.

    Na janela configuradora do projeto MRTK, expanda a seção modificar configurações, desmarque a caixa de seleção Habilitar MSBuild para Unity, verifique se todas as outras opções estão marcadas e clique no botão Aplicar para aplicar as configurações.

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > O MSBuild para Unity pode não ser compatível com todos os SDKs que você usará e pode ser complicado desabilitá-lo depois que ele tiver sido habilitado. Consequentemente, é altamente recomendável não habilitar o MSBuild para o Unity.
    
4. Crie uma nova cena. Isso pode ser feito clicando em arquivo e selecionando nova cena ". Salve-o como HLSharedProjectMain.

5. Em kit de ferramentas de realidade mista, clique em Adicionar à cena e configurar.

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Quando isso for concluído, selecione MRTK (Kit de ferramentas de realidade mista) na hierarquia. No painel Inspetor, altere o perfil de configuração MRTK para DefaultHoloLens2ConfigurationProfile.

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. Selecione MRTK (Kit de ferramentas de realidade mista) na hierarquia. No painel Inspetor, procure o script Mixed Reality Toolkit e pressione o botão "copiar & Personalizar", conforme mostrado na figura abaixo.  Um pop aparecerá depois dessa e selecione a opção clonar no menu pop-up.

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. Role para baixo e desmarque Habilitar o sistema de diagnóstico se desejar ocultar a janela de diagnóstico. É recomendável manter a janela de diagnóstico habilitada durante o desenvolvimento do aplicativo para monitorar o desempenho e, em seguida, desabilitá-lo durante as demonstrações de produção ou de aplicativo. 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. Abra as configurações de Build pressionando Control + Shift + B ou indo para arquivo-> configurações de Build. Observe que o programa está definido atualmente na plataforma autônoma de PC, Mac e Linux. Para o desenvolvimento do HoloLens 2, defina a plataforma como Plataforma Universal do Windows. Selecione-o e clique em alternar plataforma.

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. Após a conclusão, clique na caixa chamada Add Open bastidores. Agora, acesse o painel Inspetor e verifique se a caixa de seleção à direita da realidade virtual com suporte (conforme mostrado na imagem abaixo) está marcada. Verifique também se a caixa de seleção ao lado de cenas/HLSharedProjectMain também está marcada, conforme mostrado na imagem abaixo.

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. Na seção Configurações de publicação no painel Inspetor, role para baixo até recursos e verifique se as seguintes caixas de seleção estão marcadas:

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. Importe os pacotes personalizados listados:

    * [AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versão 2.1.1)
    * [MRTK. HoloLens2. Unity. tutoriais. assets. GettingStarted. 2.3.0.2. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [MRTK. HoloLens2. Unity. tutoriais. assets. AzureSpatialAnchors. 2.3.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [MRTK. HoloLens2. Unity. tutoriais. assets. MultiUserCapabilities. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >Para um lembrete sobre como configurar um projeto do Unity para âncoras espaciais do Azure, você pode consultar o tutorial [introdução ao Azure Spatial ancoras](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) que faz parte da série de tutoriais de [âncoras espaciais do Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) .


13. No painel projeto, vá para a pasta pré-fabricados. Nas etapas a seguir, você implementará algumas pré-fabricados na cena. Na pasta pré-fabricados, clique e arraste a janela pré-fabricado, depurar para a hierarquia. Quando terminar, salve o projeto clicando em arquivo e, em seguida, salve ou pressione Control + S.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    Você pode observar que um pop-up aparece ao clicar no pré-fabricado, solicitando-lhe informações sobre o TMP Essentials. Clique em importar o TMP Essentials conforme necessário. Se essa janela pop-up for exibida, talvez seja necessário excluir o pré-fabricado de sua hierarquia e arrastá-lo novamente para a hierarquia para evitar possíveis erros relacionados a texto.

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>Parabéns

Seu projeto de Unity agora está pronto para Photon. Nos próximos tutoriais, vamos criar essa cena e nosso projeto de Unity em direção a uma experiência compartilhada completa.

[Próximo tutorial: 3. conectando vários usuários](mrlearning-sharing(photon)-ch3.md)
