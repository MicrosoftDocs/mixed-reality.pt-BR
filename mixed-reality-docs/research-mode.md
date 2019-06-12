---
title: Modo de pesquisa do HoloLens
description: Usando o modo de pesquisa no HoloLens, um aplicativo pode acessar fluxos de sensor do dispositivo de chave (profundidade, o ambiente de controle e reflexibilidade IV).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modo de pesquisa, cv, rs4, pesquisa Visual computacional, pesquisa, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829936"
---
# <a name="hololens-research-mode"></a>Modo de pesquisa do HoloLens

> [!NOTE]
> Esse recurso foi adicionado como parte do [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md) para HoloLens e não está disponível em versões anteriores.

Modo de pesquisa é uma nova funcionalidade do HoloLens que fornece acesso a aplicativos para os sensores de chave no dispositivo. Como por exemplo:
- Os quatro câmeras usadas pelo sistema para construção de mapa e acompanhamento de cabeçalho de controle do ambiente.
- Duas versões dos dados de câmera de profundidade – um para detecção de perto de profundidade de (30 FPS) de alta frequência, comumente usados em mãos de controle e outro para frequência inferior (1 FPS) longe da profundidade detecção, sendo usavam atualmente por mapeamento espacial,
- Duas versões de um fluxo de IR reflexibilidade, usada pelo HoloLens para computar a profundidade, mas valioso em si mesmo como essas imagens são iluminados do HoloLens e razoavelmente não serão afetadas pela luz ambiente.

![Captura de tela de aplicativo de modo de pesquisa](images/sensor-stream-viewer.jpg)<br>
*Uma captura de realidade mista de um aplicativo de teste que exibe os fluxos de oito sensor disponíveis no modo de pesquisa*

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td>Modo de pesquisa</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a>Antes de usar o modo de pesquisa

Modo de pesquisa também é chamado: destina-se para pesquisadores acadêmicos e industriais experimentar novas ideias nos campos de pesquisa Visual computacional e robótica.  Modo de pesquisa não foi projetado para aplicativos que serão implantados em toda a empresa ou disponibilizados a Microsoft Store. A razão para isso é que o modo de pesquisa reduz a segurança do seu dispositivo e consome significativamente mais bateria do que a operação normal. Microsoft não está confirmando para dar suporte a esse modo em qualquer dispositivo futuras. Dessa forma, recomendamos que você pode usá-lo para desenvolver e testar novas ideias; No entanto, você não poderá implantar amplamente os aplicativos que usam o modo de pesquisa ou têm qualquer garantia de que ele continuará a trabalhar em futuras de hardware.

## <a name="enabling-research-mode"></a>Habilitar o modo de pesquisa

Modo de pesquisa é um modo de subpropriedades de modo de desenvolvedor. Primeiro, você precisa habilitar o modo de desenvolvedor no aplicativo configurações (**Configurações > atualização e segurança > para os desenvolvedores**):

1. Defina "Usar recursos de desenvolvedor" como **em**
2. Definido "Habilitar Portal do dispositivo" como **em**

Em seguida, usando um navegador da web que está conectado à mesma rede Wi-Fi como o HoloLens, navegue até o endereço IP do seu HoloLens (obtidas por meio **Configurações > rede e Internet > Wi-Fi > Propriedades de Hardware**). Esse é o [Portal do dispositivo](using-the-windows-device-portal.md), e você verá uma página de "Modo de pesquisa" na seção "Sistema" do portal:

![Guia de modo de pesquisa do Portal de dispositivos do HoloLens](images/ResearchModeDevPortal.png)<br>
*Modo de pesquisa no Portal de dispositivos do HoloLens*

Depois de selecionar **permitir o acesso a fluxos de sensor**, você precisará reiniciar o HoloLens. Você pode fazer isso no Portal de dispositivo, sob o item de menu "Power" na parte superior da página.

Depois que o dispositivo for reinicializado, os aplicativos que foram carregados por meio do Portal do dispositivo devem ser capazes de acessar fluxos de modo de pesquisa.

## <a name="using-sensor-data-in-your-apps"></a>Usando dados de sensor em seus aplicativos

Aplicativos podem acessar dados de fluxo de sensor, abrindo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) fluxos exatamente da mesma forma que eles acessam o fluxo de câmera de vídeo/foto. 

Todas as APIs que funcionam para o desenvolvimento HoloLens também estão disponíveis no modo de pesquisa. Em particular, o aplicativo possa saber exatamente onde HoloLens está no espaço de 6DoF no momento da captura de quadro cada sensor.

Aplicativos de exemplo que mostra como você pode acessar vários fluxos de modo de pesquisa, como usar os intrínsecos e extrinsics e como gravar fluxos estão disponíveis na [repositório HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV).

## <a name="known-issues"></a>Problemas conhecidos

Consulte a [rastreador de problemas](https://github.com/Microsoft/HololensForCV/issues) no repositório HoloLensForCV.

## <a name="see-also"></a>Consulte também

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Repositório HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)
* [Como usar o Portal de Dispositivos do Windows](using-the-windows-device-portal.md)
