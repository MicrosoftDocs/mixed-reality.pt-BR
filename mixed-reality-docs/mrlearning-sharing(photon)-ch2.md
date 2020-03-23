---
title: Tutoriais de recursos multiusuário – 2. Preparar o Unity para o desenvolvimento
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031235"
---
# <a name="2-getting-unity-ready-for-development"></a>2. Preparar o Unity para o desenvolvimento

Neste tutorial, você aprenderá a preparar e configurar o Unity para o desenvolvimento de aplicativos, incluindo importar o Mixed Reality Toolkit, definir as configurações de build e preparar sua cena.

## <a name="objectives"></a>Objetivos

* Configurar o Unity para o desenvolvimento de aplicativos
* Importe o Kit de ferramentas de realidade misturada
* Preparar a cena do projeto

## <a name="instructions"></a>Instruções

1. Baixe e salve o pacote do Unity de Fundação do Mixed Reality Toolkit clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

2. No Unity, clique no menu Ativos e selecione Importar Pacote, então clique em Pacote Personalizado.

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Selecione o pacote do Unity que você acabou de baixar do link fornecido na etapa 1. Depois que a janela pop-up importar aparecer no Unity, clique no botão Importar para começar a importar o MRTK. Isso pode levar vários minutos.

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >O pacote baixado está em pasta local em que você salvou o arquivo. A imagem acima não retrata o local em que você encontrará o pacote.

    Depois que o pacote tiver sido importado, a janela Configurador de Projeto do MRTK deverá aparecer. Se ele não aparecer, abra-o selecionando Mixed Reality Toolkit > Utilitários > Configurar Projeto do Unity no menu Unity.

    Na janela Configurador de Projeto do MRTK, expanda a seção Modificar Configurações, desmarque a caixa de seleção Habilitar MSBuild para Unity, verifique se todas as outras opções estão marcadas e clique no botão Aplicar para aplicar as configurações.

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > O MSBuild para Unity pode não ser compatível com todos os SDKs que você usará e pode ser complicado desabilitá-lo depois que ele tiver sido habilitado. Consequentemente, é altamente recomendável não habilitar o MSBuild para o Unity.
    
4. Crie uma cena. Isso pode ser feito clicando em Arquivo e selecionando Nova Cena. Salve-o como HLSharedProjectMain.

5. Em Mixed Reality Toolkit, clique em Adicionar à Cena e Configurar.

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Quando isso for concluído, selecione MRTK (Mixed Reality Toolkit) na hierarquia. No painel Inspetor, altere o perfil de configuração MRTK para DefaultHoloLens2ConfigurationProfile.

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. Selecione o MRTK (Mixed Reality Toolkit) da hierarquia. No painel do inspetor, procure o Script do Mixed Reality Toolkit e pressione o botão "Copiar e Personalizar", como mostra a figura abaixo.  Um pop aparecerá depois disso. Selecione a opção Clonar no menu pop-up.

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. Role para baixo e desmarque Habilitar Sistema de Diagnóstico se você quiser ocultar a janela de diagnóstico. É recomendável manter a janela de diagnóstico habilitada durante o desenvolvimento do aplicativo para monitorar o desempenho e, em seguida, desabilitá-la durante as demonstrações de produção ou de aplicativo. 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. Abra as configurações de build pressionando Control+Shift+B ou acessando Arquivo->Configurações de Build. Observe que o programa está definido atualmente na plataforma autônoma de PC, Mac e Linux. Para o desenvolvimento do HoloLens 2, defina a plataforma como Plataforma Universal do Windows. Selecione-a e clique em alternar plataforma.

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. Após a conclusão, clique na caixa chamada Adicionar Cenas Abertas. Agora, acesse o painel Inspetor e verifique se a caixa de seleção à direita de Realidade Virtual Compatível (conforme mostra a imagem abaixo) está marcada. Verifique também se a caixa de seleção ao lado de cenas/HLSharedProjectMain também está marcada, conforme mostrado na imagem abaixo.

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. Na seção Configurações de Publicação no painel Inspetor, role para baixo até Funcionalidades e verifique se as seguintes caixas de seleção estão marcadas:

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. Importe os pacotes personalizados listados:

    * [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versão 2.1.1)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >Para um lembrete sobre como configurar um projeto do Unity para Âncoras Espaciais do Azure, veja o tutorial [Introdução às Âncoras Espaciais do Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) que faz parte da série de tutoriais [Âncoras Espaciais do Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1).


13. No painel Projeto, vá para a pasta Pré-Fabricados. Nas etapas a seguir, você implementará alguns Pré-Fabricados na cena. Na pasta Pré-Fabricados, clique e arraste a Janela de Depuração do pré-fabricado para a hierarquia. Quando terminar, salve o projeto clicando em Arquivo e, em seguida, escolha Salvar ou pressione Control+S.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    Você pode observar que um pop-up aparece ao clicar no pré-fabricado solicitando informações sobre o TMP Essentials. Clique em Importar TMP Essentials conforme necessário. Se essa janela pop-up for exibida, talvez seja necessário excluir o pré-fabricado da hierarquia e arrastá-lo novamente para a hierarquia para evitar possíveis erros relacionados a texto.

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>Parabéns

Seu Projeto do Unity agora está pronto para Photon. Nos próximos tutoriais, vamos criar essa cena e nosso projeto do Unity para uma experiência compartilhada completa.

[Próximo tutorial: 3. Conectar vários usuários](mrlearning-sharing(photon)-ch3.md)
