---
title: Modo de pesquisa do HoloLens
description: Usando o modo de pesquisa no HoloLens, um aplicativo pode acessar fluxos de sensor de dispositivo de chave (profundidade, acompanhamento de ambiente e IR-reflectivity).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modo de pesquisa, CV, RS4, visão computacional, pesquisa, HoloLens
ms.openlocfilehash: 307df0c226221422f13af09d8f4944c22ead3865
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438309"
---
# <a name="hololens-research-mode"></a>Modo de pesquisa do HoloLens

> [!NOTE]
> Esse recurso foi adicionado como parte da [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md) para o HoloLens e não está disponível em versões anteriores.

O modo de pesquisa é um novo recurso do HoloLens que fornece acesso de aplicativo aos sensores de chave no dispositivo. São elas:
- As quatro câmeras de acompanhamento de ambiente usadas pelo sistema para criação de mapa e acompanhamento de cabeçalho.
- Duas versões dos dados da câmera de profundidade – uma para a detecção de alta frequência (30 FPS) de profundidade, normalmente usada e a outra para a detecção de profundidade de extrema frequência (1-5 FPS), atualmente usada pelo mapeamento espacial,
- Duas versões de um fluxo IR-reflectivity, usadas pelo HoloLens para computar a profundidade, mas valiosas por si só, à medida que essas imagens são acesas do HoloLens e não afetam razoavelmente por luz ambiente.

captura de tela do aplicativo do modo de pesquisa ![](images/sensor-stream-viewer.jpg)<br>
*Uma captura de realidade misturada de um aplicativo de teste que exibe os oito fluxos de sensor disponíveis no modo de pesquisa*

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Modo de pesquisa</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a>Antes de usar o modo de pesquisa

O modo de pesquisa é bem nomeado: destina-se a pesquisadores acadêmicos e industriais experimentando novas ideias nos campos de Pesquisa Visual Computacional e robótica.  O modo de pesquisa não se destina a aplicativos que serão implantados em uma empresa ou disponibilizados no Microsoft Store. O motivo disso é que o modo de pesquisa reduz a segurança do seu dispositivo e consome significativamente mais energia da bateria do que a operação normal. A Microsoft não está confirmando o suporte a esse modo em nenhum dispositivo futuro. Portanto, recomendamos que você o use para desenvolver e testar novas ideias; no entanto, você não poderá implantar amplamente aplicativos que usam o modo de pesquisa ou ter qualquer garantia de que ele continuará a funcionar no hardware futuro.

## <a name="enabling-research-mode"></a>Habilitando o modo de pesquisa

O modo de pesquisa é um submodo do modo de desenvolvedor. Primeiro, você precisa habilitar o modo de desenvolvedor no aplicativo Configurações (**configurações > atualização & segurança > para desenvolvedores**):

1. Defina "usar recursos de desenvolvedor" como **on**
2. Defina "habilitar o portal do dispositivo" como **ativado**

Em seguida, usando um navegador da Web que está conectado à mesma rede Wi-Fi que o seu HoloLens, navegue até o endereço IP do seu HoloLens (obtido por meio **das configurações > rede & Internet > Wi-Fi > Propriedades de hardware**). Este é o [portal do dispositivo](using-the-windows-device-portal.md)e você encontrará uma página "modo de pesquisa" na seção "sistema" do portal:

guia modo de pesquisa ![do portal do dispositivo de HoloLens](images/ResearchModeDevPortal.png)<br>
*Modo de pesquisa no portal do dispositivo do HoloLens*

Depois de selecionar **permitir o acesso aos fluxos de sensor**, você precisará reinicializar o HoloLens. Você pode fazer isso no portal do dispositivo, sob o item de menu "Power" na parte superior da página.

Depois que o dispositivo for reinicializado, os aplicativos que foram carregados por meio do portal do dispositivo deverão ser capazes de acessar os fluxos do modo de pesquisa.

## <a name="using-sensor-data-in-your-apps"></a>Usando dados de sensor em seus aplicativos

Os aplicativos podem acessar dados de fluxo do sensor abrindo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) fluxos exatamente da mesma maneira que acessam o fluxo de foto/vídeo da câmera. 

Todas as APIs que funcionam para o desenvolvimento do HoloLens também estão disponíveis no modo de pesquisa. Em particular, o aplicativo pode saber precisamente onde o HoloLens está no espaço 6DoF em cada tempo de captura do quadro do sensor.

Aplicativos de exemplo mostrando como você acessa os vários fluxos do modo de pesquisa, como usar os intrínsecos e as extrínsecos e como registrar os fluxos estão disponíveis no [repositório GitHub do HoloLensForCV](https://github.com/Microsoft/HoloLensForCV).

## <a name="known-issues"></a>Problemas conhecidos

Consulte o Issue [Tracker](https://github.com/Microsoft/HololensForCV/issues) no repositório HoloLensForCV.

## <a name="see-also"></a>Consulte também

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Repositório GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [Como usar o Portal de Dispositivos do Windows](using-the-windows-device-portal.md)
