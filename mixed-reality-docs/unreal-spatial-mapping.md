---
title: Mapeamento espacial no Unreal
description: Guia para usar o mapeamento espacial no Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial mapping
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840075"
---
# <a name="spatial-mapping-in-unreal"></a>Mapeamento espacial no Unreal

Para habilitar o mapeamento espacial no HoloLens, marque a funcionalidade "Percepção Espacial" no editor do Unreal em Configurações do Projeto > Plataforma > HoloLens > Funcionalidades.  

Para optar pelo uso do mapeamento espacial em um jogo do HoloLens, habilite "Gerar Dados de Malha de Geometria Rastreada" no ARSessionConfig.  Dessa maneira, o plug-in do HoloLens obterá dados de mapeamento espacial de maneira assíncrona e os entregará ao Unreal por meio do MRMesh. 

![Armazenamento de âncoras espaciais pronto](images/unreal-spatialmapping-arsettings.PNG)

Para ver uma visualização de depuração da malha de mapeamento espacial, habilite a caixa de seleção "Renderizar Dados de Malha no Delineado" no ARSessionConfig para ver um contorno delineado branco de cada triângulo no MRMesh. 

Em Configurações do Projeto > Plataforma > HoloLens > Mapeamento Espacial, os seguintes parâmetros podem ser modificados para atualizar o comportamento do runtime do mapeamento espacial: 

![Configurações do projeto de âncoras espaciais](images/unreal-spatialmapping-projectsettings.PNG)

A opção Máximo de Triângulos por Metro Cúbico atualizará a densidade dos triângulos na malha de mapeamento espacial.  A opção Tamanho do Volume de Malha Espacial indica o tamanho do cubo em volta do jogador para renderizar e atualizar os dados de mapeamento espacial.  Se for previsto que o ambiente do runtime do aplicativo será grande, esse campo precisará ser grande para corresponder ao espaço do mundo real.  Por outro lado, se o aplicativo precisar apenas posicionar hologramas nas superfícies imediatamente próximas do usuário, esse campo poderá ser menor.  À medida que o usuário se movimenta pelo mundo, o volume de mapeamento espacial se moverá com ele. 

Para obter acesso ao MRMesh em runtime, primeiro adicione um Componente AR Trackable Notify a um ator do Blueprint: 

![AR Trackable Notify de âncoras espaciais](images/unreal-spatialmapping-artrackablenotify.PNG)

Em seguida, acesse os detalhes do componente e clique no botão "+" verde nos eventos a serem monitorados. 

![Eventos de âncoras espaciais](images/unreal-spatialmapping-events.PNG)

Nesse caso, monitoramos o evento On Add Tracked Geometry procurando por malhas válidas do mundo que correspondam aos dados de mapeamento espacial e alterem o material da malha: 

![Exemplo de âncoras espaciais](images/unreal-spatialmapping-example.PNG)

No C++, podemos assinar o delegado OnTrackableAdded para obter o ARTrackedGeometry assim que ele estiver disponível.  Há delegados semelhantes para eventos atualizados e removidos: AddOnTrackableUpdatedDelegate_Handle e AddOnTrackableRemovedDelegate_Handle. 

![Código de exemplo de âncoras espaciais em C++](images/unreal-spatialmapping-examplecode.PNG)

O build.cs do projeto deve ter "AugmentedReality" na lista PublicDependencyModuleNames para incluir "ARBlueprintLibrary.h" e "MRMesh" para inspecionar o componente MRMesh do UARTrackedGeometry. 

O mapeamento espacial não é o único tipo de dados que é exibido por meio do ARTrackedGeometries, portanto, primeiro verificamos se o EARObjectClassification é Mundo, o que indica que isso é geometria de mapeamento espacial. 

## <a name="see-also"></a>Veja também
* [Mapeamento espacial](spatial-mapping.md)
