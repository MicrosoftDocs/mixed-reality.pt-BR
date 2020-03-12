---
title: Player de comunicação remota do Holographic
description: O Holographic Remoting Player é um aplicativo complementar que se conecta a aplicativos de PC e jogos que dão suporte à comunicação remota do Holographic. O Holographicing Remoting transmite o conteúdo do Holographic de um PC para o Microsoft HoloLens em tempo real, usando uma conexão Wi-Fi.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: 88a9aa0bb058776a32016e51fc22bcb73f08ab85
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092376"
---
# <a name="holographic-remoting-player"></a>Player de comunicação remota do Holographic

>[!IMPORTANT]
>A comunicação remota do Holographic para o HoloLens 2 é uma alteração de versão principal. [Os aplicativos remotos para o **hololens (1ª gen)** ](add-holographic-remoting.md) devem usar o pacote NuGet versão **1. x.** x e [os aplicativos remotos para o **HoloLens 2** ](holographic-remoting-create-host.md) devem usar **2. x. x**. Isso significa que os aplicativos remotos escritos para o HoloLens 2 não são compatíveis com o HoloLens (1º gen) e vice-versa.

O [Holographic Remoting Player](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) é um aplicativo complementar que se conecta a aplicativos de PC e jogos que dão suporte à comunicação remota do Holographic. O Holographicing Remoting transmite o conteúdo do Holographic de um PC para o Microsoft HoloLens em tempo real, usando uma conexão Wi-Fi.

O player de comunicação remota do Holographic só pode ser usado com aplicativos de PC projetados especificamente para dar suporte à comunicação remota do Holographic.

O player de comunicação remota do Holographic está disponível para o HoloLens (1º gen) e o HoloLens 2.  Aplicativos de PC com suporte para comunicação remota Holographic com o HoloLens precisam ser atualizados para dar suporte a comunicação remota Holographic com o HoloLens 2. Entre em contato com seu provedor de aplicativos se tiver dúvidas sobre quais versões têm suporte.

## <a name="connecting-to-the-holographic-remoting-player"></a>Conectando-se ao Player de comunicação remota do Holographic

Siga as instruções do aplicativo para se conectar ao Player de comunicação remota do Holographic. Você precisará inserir o endereço IP do seu dispositivo HoloLens, que pode ser visto na tela principal do reprodutor de comunicação remota, da seguinte maneira:

![Player de comunicação remota do Holographic](images/holographicremotingplayer.png)

Sempre que vir a tela principal, você saberá que não tem um aplicativo conectado.

Observe que a conexão remota Holographic **não está criptografada**. Você sempre deve usar a comunicação remota do Holographic em uma conexão Wi-Fi segura na qual você confia.

## <a name="quality-and-performance"></a>Qualidade e desempenho

A qualidade e o desempenho da sua experiência variam com base em três fatores:
* **A experiência do Holographic que você está executando** -aplicativos que processam alta resolução ou conteúdo altamente detalhado pode exigir um PC mais rápido ou uma conexão sem fio mais rápida.
* **Hardware do seu PC** -seu PC precisa ser capaz de executar e codificar sua experiência com o holographic em 60 quadros por segundo. Para uma placa gráfica, geralmente recomendamos um GeForce GTX 970 ou o AMD Radeon R9 290 ou superior. Novamente, sua experiência específica pode exigir um cartão maior ou menor.
* **Sua conexão Wi-Fi** -sua experiência com o Holographic é transmitida por Wi-Fi. Use uma rede rápida com baixo congestionamento para maximizar a qualidade. Usar um computador conectado por um cabo Ethernet, em vez de Wi-Fi, também pode melhorar a qualidade.

## <a name="diagnostics"></a>Diagnóstico

Para medir a qualidade de sua conexão, diga **"habilitar o diagnóstico"** enquanto estiver na tela principal do Holographic Remoting Player. Quando os diagnósticos estão habilitados, no **HoloLens (1º gen)** , o aplicativo mostrará:

* **FPS** -o número médio de quadros renderizados que o player de comunicação remota está recebendo e renderizando por segundo. O ideal é de 60 FPS.
* **Latência** -a quantidade média de tempo que leva para um quadro passar do seu PC para o HoloLens. Quanto menor for o melhor. Isso é amplamente dependente de sua rede Wi-Fi.

No **HoloLens 2** , o aplicativo mostrará:

![Diagnóstico do player de comunicação remota do Holographic](images/holographicremotingplayer-diag.png)

* **Render** -o número de quadros processados pelo Player de comunicação remota durante o último segundo. Observe que isso é independente do número de quadros que chegaram pela rede (consulte quadros de **vídeo**). Além disso, o tempo de Delta médio/máximo de renderização em milissegundos no último segundo entre os quadros renderizados é exibido.

* **Quadros de vídeo** -o primeiro número exibido são os quadros de vídeo ignorados, o segundo são quadros de vídeo reutilizados e o terceiro recebe quadros de vídeo. Todos os números representam a contagem no último segundo.
    * ```Received frames``` é o número de quadros de vídeo que chegaram no último segundo. Em condições normais, isso deve ser 60, mas se não for, um indicador de que os quadros serão descartados devido a problemas de rede ou o lado remoto/remoto não produzirá quadros com a taxa esperada.
    * ```Reused frames``` é a contagem de quadros de vídeo usados mais de uma vez no último segundo. Por exemplo, se os quadros de vídeo chegarem atrasados, o loop de renderização do Player ainda renderizará um quadro, mas precisará *reutilizar* o quadro de vídeo que já foi usado para o quadro anterior.
    * ```Skipped frames``` é a contagem de quadros de vídeo que não foram usados pelo loop de renderização do Player. Por exemplo, a tremulação de rede pode ter o efeito de que os quadros de vídeo recebidos não são mais distribuídos uniformemente. Por exemplo, se alguns estiverem atrasados e outros chegarem no tempo, com o resultado, eles não terão mais um Delta de 16,66 milissegundos ao serem executados em 60Hz. Pode ocorrer que mais de um quadro chega entre dois tiques do loop de renderização do Player. Nesse caso, o Player *ignora* um ou mais quadros, pois ele deve sempre exibir o quadro de vídeo mais recente recebido.

    >[!NOTE]
    >Quando voltada para a variação da rede, os quadros ignorados e reutilizados geralmente são aproximadamente os mesmos. Por outro lado, se você ver apenas os quadros ignorados, esse é um indicador de que o Player não atingiu sua taxa de quadros de destino. Nesse caso, você deve ficar atento ao tempo máximo de processamento Delta ao diagnosticar problemas.

* **Quadros de vídeo Delta** -o Delta mínimo/máximo entre quadros de vídeo recebidos no último segundo. Esse número geralmente se correlaciona com os quadros ignorados/reutilizados em caso de problemas causados pela tremulação da rede.
* **Latência** -o tempo de conclusão médio em milissegundos no último segundo. O retorno nesse contexto significa o tempo de envio de dados de pose/sensor do HoloLens para o lado remoto/remoto, até exibir o quadro de vídeo para os dados de pose/telemetria na tela do HoloLens.
* **Quadros de vídeo descartados** -o número de quadros de vídeo descartados no último segundo e desde que uma conexão foi estabelecida. A principal causa de quadros de vídeo descartados é quando um quadro de vídeo não chega em ordem e, por esse motivo, precisa ser descartado, pois já existe um mais recente. Isso é semelhante a *quadros descartados* , mas a causa está em um nível inferior na pilha de comunicação remota. Os quadros de vídeo descartados são esperados apenas em condições de rede muito ruins.



Na tela principal, você pode dizer **"desabilitar o diagnóstico"** para desativar o diagnóstico.

## <a name="pc-system-requirements"></a>Requisitos do sistema do PC
* Seu computador **deve** estar executando a atualização de aniversário do Windows 10 ou mais recente.
* Recomendamos uma placa gráfica GeForce GTX 970 ou AMD Radeon R9 290 ou superior.
* Recomendamos que você conecte seu PC à sua rede por meio de Ethernet para reduzir o número de saltos sem fio.

## <a name="see-also"></a>Consulte também
* [HoloLens (1º gen): Adicionar comunicação remota do Holographic](add-holographic-remoting.md)
* [HoloLens 2: escrevendo um aplicativo remoto de comunicação remota do Holographic](holographic-remoting-create-host.md)
* [Termos de licença de software de comunicação remota holográfica](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
