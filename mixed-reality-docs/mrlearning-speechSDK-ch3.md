---
title: TUTORIAIS dos serviços de fala do Azure-3. Adicionando o componente de tradução de fala dos serviços cognitivas do Azure
description: Neste curso, você aprenderá a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: dc5300b51ccb151a2e38f9d15b84a4a9031e2bb4
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143229"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. adicionando o componente de tradução de fala dos serviços cognitivas do Azure

Neste tutorial, você aprenderá sobre o componente de tradução de fala dos serviços cognitivas do Azure do seu projeto, além de como traduzir em três idiomas diferentes.

## <a name="instructions"></a>Instruções

1. Selecione o objeto Lunarcom_Base na hierarquia e clique em Adicionar componente no painel inspetor. Procure e selecione reconhecedor de tradução do Lunarcom.

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    Desabilite o simulador de modo offline.

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    >Antes de prosseguir, verifique se o simulador do modo offline está desabilitado (conforme mostrado na imagem acima) antes de testar o conversor do SDK de fala. Para traduzir, você deve estar conectado à Internet.

2. Clique na lista suspensa no reconhecedor de tradução do Lunarcom e selecione o idioma para o qual você deseja traduzir.

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. Execute o aplicativo e teste o tradutor clicando no botão satélite e comece a falar. Pressione o botão satélite novamente para interromper o reconhecimento. Veja abaixo um exemplo de como deve ser sua cena. Fique à vontade para alterar o idioma na lista suspensa "idioma de destino" (consulte a imagem acima) para explorar a tradução em outros idiomas.

    Abaixo está um exemplo de como deve ser a aparência de sua cena:

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Parabéns

Agora, seu projeto pode traduzir com êxito as palavras que você fala em vários idiomas diferentes. Fique à vontade para brincar com os idiomas e teste a precisão da tradução.

[Próximo tutorial: 4. Configurando a intenção e o reconhecimento de idioma natural](mrlearning-speechSDK-ch4.md)
