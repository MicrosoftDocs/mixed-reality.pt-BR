---
title: Calibragem
description: A calibragem do IPD (distância interpupillary) pode melhorar a qualidade dos visuais. Os headsets do HoloLens e do Windows Mixed realm de imersão oferecem maneiras de personalizar o IPD.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: calibragem, conforto, visuais, qualidade, IPD
ms.openlocfilehash: 354d7eb74666471f24a6b5774e5772260b1e3570
ms.sourcegitcommit: 5d3be2d7569d912011ea114c0a283bc3c635d5df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69979478"
---
# <a name="improve-visual-quality-and-comfort"></a>Aprimore a qualidade visual e o conforto
O HoloLens, o HoloLens 2 e os headsets de imersão de realidade misturada do Windows oferecem maneiras diferentes de melhorar a qualidade da experiência visual. 

## <a name="hololens-2"></a>Hololens 2

### <a name="calibration"></a>Calibragem

O Hololens 2 foi projetado para fornecer as imagens visuais de qualidade mais alta e o conforto para nossos clientes. A tecnologia de controle de olho é usada para melhorar a experiência do usuário de ver e interagir com o ambiente virtual.  
No HoloLens 2, você será solicitado a calibrar seus visuais durante a configuração do dispositivo. Os usuários são solicitados a examinar o conjunto de destinos fixação da. Isso permite que o dispositivo ajuste a renderização de holograma para o usuário para garantir que os hologramas posicionados com precisão, a experiência de exibição 3D confortável e a qualidade de exibição aprimorada. Todos os ajustes ocorrem em tempo real sem necessidade de ajuste manual. Usando os olhos como pontos de referência, o dispositivo é ajustado para cada usuário e os visuais são ajustados conforme o fone de ouvido muda um pouco durante o uso. O controle de posição de olho é usado internamente pelo sistema e os desenvolvedores não precisam fazer nada para aproveitar esse recurso. Essas informações não estão disponíveis para os desenvolvedores. No Hololens 2, a execução da calibragem também garante o acompanhamento preciso de olhar para cada usuário. O acompanhamento ocular permite que os aplicativos acompanhem para que local o usuário está olhando em tempo real. Esse é o principal recurso que os desenvolvedores podem aproveitar para habilitar um nível totalmente novo de contexto, compreensão humana e interações dentro da experiência do Holographic.  
A calibragem é armazenada localmente no dispositivo e não está associada a nenhuma informação de conta. Não há registro de quem usou o dispositivo sem calibragem. Isso significa que novos usuários receberão uma solicitação para calibrar visuais quando usarem o dispositivo pela primeira vez, bem como os usuários que optaram pela recalibração anteriormente ou se a calibragem não tiver sido bem-sucedida. A calibragem sempre pode ser excluída do dispositivo em **configurações** > **rastreador**de**privacidade** > . 

### <a name="calibration-failures"></a>Falhas de calibragem

A calibragem deve funcionar para a maioria dos usuários, mas há casos em que o usuário pode não conseguir calibrar com êxito.  
Alguns exemplos de falhas de calibragem são devido a:
- Usuário recebendo distraídos e não seguindo os destinos de calibragem durante a experiência de calibragem
- Visor ou visor de dispositivo sujo ou arranhado não está posicionado corretamente 
- Óculos sujos ou arranhados
- Certos tipos de lentes de contato e óculos (lentes de contato coloridas, algumas lentes de contato toric, óculos de bloqueio de IR, alguns óculos altos de receita, óculos, etc.)
- Composição mais pronunciada, algumas extensões Eyelash
- Occlusions de olho e/ou visor do dispositivo (cabelo, alguns quadros eyeglass grossos)
- Olho physiology, certas condições de olho e/ou cirurgia de olho (alguns olhos estreitos, longa eyelashes, amblyopia, Nystagmus, alguns casos de LASIK ou outros olhos Surgeries, etc.)

Se a calibragem não for bem-sucedida, tente uma destas correções: 
- Limpar o visor do dispositivo
- Limpar os óculos
- Envie seu dispositivo com o visor todo o caminho
- Certifique-se de que nada esteja obstruindo os sensores ou seus olhos (por exemplo, cabelo) 
- Verifique se há luz suficiente em sua sala e se você não está sob a luz do sol direta
- Verifique se você está seguindo cuidadosamente os destinos durante a calibragem

Se você seguiu todas as diretrizes e a calibragem ainda falha, você pode desabilitar o prompt de calibragem em **configurações** > calibragem do**sistema** > . ' Quando uma nova pessoa usa esse Hololens, pedir automaticamente para executar a calibragem de olho ' deve ser ajustada. Entenda que isso pode resultar na pior qualidade de renderização de holograma e discomfort.

### <a name="launching-the-calibration-app-from-settings"></a>Iniciando o aplicativo de calibragem de configurações
1. Use o gesto de início para acessar o [menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Selecione **todos os aplicativos** para exibir todos os aplicativos se **as configurações** não estiverem fixadas no início.
3. **Configurações**de inicialização.
4. Navegue até calibragem de**olho** do **sistema** >  > e selecione executar calibragem de **olho**.

### <a name="calibration-when-sharing-a-device--session"></a>Calibragem ao compartilhar um dispositivo/sessão

O Hololens 2 pode ser compartilhado entre pessoas, sem a necessidade de que cada pessoa passe pela configuração do dispositivo. O Hololens 2 solicitará que o usuário calibre os visuais quando o dispositivo for colocado na cabeça se o usuário for novo no dispositivo. Se o usuário tiver calibrado os visuais anteriormente no dispositivo, a exibição será ajustada diretamente para qualidade e uma experiência de exibição confortável quando o usuário colocar o dispositivo no cabeçalho. 


## <a name="hololens"></a>Hololens

A calibragem do IPD (distância interpupillary) pode melhorar a qualidade dos visuais.

### <a name="during-setup"></a>Durante a instalação

![Tela de alinhamento de dedo de IPD na segunda etapa](images/ipd-finger-alignment-300px.jpg)<br>

*Tela de alinhamento de dedo de IPD na segunda etapa*

No HoloLens, você será solicitado a calibrar seus visuais durante a instalação. Isso permite que o dispositivo ajuste a exibição de holograma de acordo com a [Interpupillary de distância](https://en.wikipedia.org/wiki/Interpupillary_distance) do usuário (IPD). Com um IPD incorreto, os hologramas podem aparecer instáveis ou em uma distância incorreta.

Depois que a Cortana apresenta, a primeira etapa de instalação é a calibragem. É recomendável que você conclua a etapa de calibragem durante essa fase de instalação, mas ela pode ser ignorada aguardando até que o Cortana solicite que você diga "Skip" para continuar.

Os usuários são solicitados a alinhar seus dedos com uma série de seis destinos por olho. Por meio desse processo, o HoloLens define o IPD correto para o usuário. Se a calibragem precisar ser atualizada ou ajustada para um novo usuário, ela poderá ser executada fora da instalação usando o aplicativo de calibragem.

### <a name="calibration-app"></a>Aplicativo de calibragem

A calibragem pode ser executada a qualquer momento por meio do aplicativo de calibragem. O aplicativo de calibragem é instalado por padrão e pode ser acessado no menu iniciar ou por meio do aplicativo configurações. A calibragem é recomendada se você quiser melhorar a qualidade de seus visuais ou calibrar visuais para um novo usuário.

**Iniciando o aplicativo a partir do início**
1. Use a [flor](gestures.md#bloom) para começar a usar o [menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Selecione **+** para exibir todos os aplicativos.
3. Iniciarcalibragem.

![Acessando o aplicativo de calibragem do Shell](images/calibration-shell.png)

![O aplicativo de calibragem exibido como um cubo ao vivo após ser iniciado](images/calibration-livecube-200px.png)

**Iniciando o aplicativo com base nas configurações**
1. Use a [flor](gestures.md#bloom) para começar a usar o [menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Selecione **+** para exibir todos os aplicativos se **as configurações** não estiverem fixadas no início.
3. **Configurações**de inicialização.
4. Navegue até**utilitários** do **sistema** > e selecione **abrir**calibragem.

![Iniciando o aplicativo de calibragem no aplicativo de configurações](images/calibration-settings-500px.jpg)


## <a name="immersive-headsets"></a>Headsets imersivos

Para alterar o IPD em seu headset, abra o aplicativo Configurações e navegue até a **realidade** > misturada**fone de ouvido exibir** e mover o controle deslizante. Você verá as alterações em tempo real em seu headset. Se você conhece seu IPD, talvez de uma visita à optometrist, você também pode inseri-lo diretamente.

Você também pode ajustar essa configuração acessando **configurações** > **combinação de realidade** > com**fone de ouvido** no seu PC.

Se o headset não oferecer suporte à personalização do IPD, essa configuração será desabilitada.

## <a name="see-also"></a>Consulte também
* [Considerações sobre o ambiente para HoloLens](environment-considerations-for-hololens.md)
