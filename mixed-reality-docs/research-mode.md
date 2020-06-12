---
title: Modo de pesquisa do HoloLens
description: Usando o modo de pesquisa no HoloLens, um aplicativo pode acessar fluxos de sensor de dispositivo de chave (profundidade, acompanhamento de ambiente e IR-reflectivity).
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
keywords: modo de pesquisa, CV, RS4, pesquisa Visual computacional, Research, HoloLens, HoloLens 2
ms.openlocfilehash: 62b82e3a36452d4b104bf04999e556ec19d2a5e3
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720392"
---
# <a name="hololens-research-mode"></a>Modo de pesquisa do HoloLens

## <a name="overview"></a>Visão geral

O modo de pesquisa foi introduzido no HoloLens de primeira geração para dar acesso aos principais sensores no dispositivo, especificamente para aplicativos de pesquisa que não se destinam à implantação. Agora você pode coletar dados das seguintes entradas:

* **Câmeras de rastreamento de ambiente leve visíveis** – usadas pelo sistema para rastreamento de cabeçalho e criação de mapa.
* **Câmera de profundidade** – opera em dois modos:  
    + Detecção de curto-short, de alta frequência (30 FPS) usada para [acompanhamento à mão](interaction-fundamentals.md)
    + Detecção de longo alcance, de baixa frequência (1-5 FPS) de longa profundidade usada pelo [mapeamento espacial](spatial-mapping.md)
* **Duas versões do fluxo ir-reflectivity** -usadas pelo HoloLens para calcular a profundidade. Essas imagens são iluminadas por infravermelho e não são afetadas pela luz visível de ambiente.

Se você estiver usando um HoloLens 2, também poderá acessar as seguintes entradas:

* **Acelerômetro** – usado pelo sistema para determinar a aceleração linear ao longo dos eixos X, Y e Z e gravidade.
* **Giro** – usado pelo sistema para determinar rotações.
* **Magnetômetro** – usado pelo sistema para estimar a orientação absoluta.

![Captura de tela do aplicativo de modo de pesquisa](images/sensor-stream-viewer.jpg)<br>
*Uma captura de realidade misturada de um aplicativo de teste que exibe os oito fluxos de sensor disponíveis no modo de pesquisa*

> [!NOTE]
> O recurso de modo de pesquisa foi adicionado como parte da [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md) para o HoloLens e não está disponível em versões anteriores.

## <a name="usage"></a>Uso

O modo de pesquisa foi projetado para pesquisadores acadêmicos e industriais que exploram novas ideias nos campos de Pesquisa Visual Computacional e robótica.  Ele não se destina a aplicativos implantados em ambientes corporativos ou disponíveis por meio do Microsoft Store ou de outros canais de distribuição.

Além disso, a Microsoft não fornece garantias de que o modo de pesquisa ou funcionalidade equivalente terá suporte em atualizações futuras de hardware ou sistema operacional. No entanto, isso não deve impedir que você o use para desenvolver e testar novas ideias!

## <a name="security-and-performance"></a>Segurança e desempenho

Lembre-se de que habilitar o modo de pesquisa usa mais energia da bateria do que usar o HoloLens 2 em condições normais. Isso é verdadeiro mesmo que o aplicativo que usa os recursos do modo de pesquisa não esteja em execução.  Habilitar esse modo também pode reduzir a segurança geral do seu dispositivo, pois os aplicativos podem indevidamente os dados do sensor.  Você pode encontrar mais informações sobre a segurança do dispositivo nas [perguntas frequentes sobre segurança do HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).  


## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>1ª Gen do HoloLens</strong></a></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td>Câmeras de acompanhamento de cabeçalho</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Profundidade & câmera IR</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Acelerômetro</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Giroscópio</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Magnetômetro</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> O suporte ao modo de pesquisa para o HoloLens 2 deve estar disponível na visualização pública em julho de 2020 e incluirá todos os recursos listados acima. Consulte novamente para obter mais informações. 

## <a name="enabling-research-mode"></a>Habilitando o modo de pesquisa

O modo de pesquisa é uma extensão do modo de desenvolvedor. Antes de iniciar, os recursos do desenvolvedor do dispositivo precisam ser habilitados para acessar as configurações do modo de pesquisa: 

* Abra o **menu iniciar > configurações** e selecione **atualizações**.
* Selecione **para desenvolvedores** e habilite o **modo de desenvolvedor**.
* Role para baixo e habilite o **Portal de Dispositivos**.

Depois que os recursos do desenvolvedor estiverem habilitados, [Conecte-se ao portal do dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar os recursos do modo de pesquisa.

Na *1ª Gen do HoloLens*:

* Vá para o **sistema > modo de pesquisa** no **portal do dispositivo**.
* Selecione **permitir acesso ao fluxo do sensor**.
* Reinicie o dispositivo a partir do item de menu de **energia** na parte superior da página.

Depois de reiniciar o dispositivo, os aplicativos carregados por meio do portal do **dispositivo** poderão acessar os fluxos do modo de pesquisa.

![Guia modo de pesquisa do portal do dispositivo do HoloLens](images/ResearchModeDevPortal.png)<br>
*Janela do modo de pesquisa no portal do dispositivo do HoloLens*

## <a name="using-sensor-data-in-your-apps"></a>Usando dados de sensor em seus aplicativos

*1ª Gen do HoloLens*

Os aplicativos podem acessar os dados de fluxo do sensor da mesma maneira que os fluxos de foto e câmera de vídeo são acessados por meio de [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197). 

Todas as APIs que funcionam para o desenvolvimento do HoloLens também estão disponíveis no modo de pesquisa. Em particular, o aplicativo sabe precisamente onde o HoloLens está no espaço 6DoF em cada tempo de captura do quadro do sensor.

Você pode encontrar aplicativos de exemplo sobre como acessar os vários fluxos do modo de pesquisa, como usar os [intrínsecos e as extrínsecos](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)e como registrar fluxos no repositório do [repositório GitHub do HoloLensForCV](https://github.com/Microsoft/HoloLensForCV) .

 > [!NOTE]
 > Neste momento, o exemplo HoloLensForCV não funciona no HoloLens 2.

## <a name="known-issues"></a>Problemas conhecidos

Você pode usar o Issue [Tracker](https://github.com/Microsoft/HololensForCV/issues) no repositório HoloLensForCV para seguir os problemas conhecidos.

## <a name="see-also"></a>Veja também

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Repositório GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [Como usar o Portal de Dispositivos do Windows](using-the-windows-device-portal.md)
