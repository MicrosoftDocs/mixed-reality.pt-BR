---
title: Estudo de caso - lições da cozinha do Lowe
description: A equipe do HoloLens deseja compartilhar algumas das práticas recomendadas derivadas do projeto do HoloLens do Lowe.
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, do Lowe, HoloLens, cozinha, estudo de caso
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589541"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>Estudo de caso - lições da cozinha do Lowe

A equipe do HoloLens deseja compartilhar algumas das práticas recomendadas derivadas do projeto do HoloLens do Lowe. Veja abaixo um vídeo do HoloLens do Lowe projetada é demonstrado na palestra de Ignite de 2016 do Satya.
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Práticas recomendadas do HoloLens do Lowe

Os dois vídeos abordam as práticas recomendadas derivadas do piloto de HoloLens do Lowe que nos repositórios do dois Lowe desde abril de 2016. Os tópicos principais são:
* Maximizar o desempenho de um dispositivo móvel
* Criar métodos de experiência do usuário com um quadro completo holográfico (2ª talk)
* Alinhamento de precisão (2ª talk)
* Compartilhado holográfica experiências (2ª talk)
* Interagindo com os clientes (2ª talk)

## <a name="video-1"></a>Vídeo 1

**Maximizar o desempenho de um dispositivo móvel** HoloLens é um dispositivo de forma independente com todo o processamento que estão ocorrendo no dispositivo. Isso exige uma plataforma móvel e uma mentalidade semelhante à criação de aplicativos móveis. A Microsoft recomenda que o seu aplicativo HoloLens manter 60FPS para fornecer uma experiência deliciosa para seus usuários. Ter FPS baixa pode resultar em hologramas instáveis.

Algumas das coisas mais importantes para observar ao desenvolver em HoloLens é otimização ativo/eliminação, usando os sombreadores personalizados (disponível gratuitamente na [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)). Outra consideração importante é medir a taxa de quadros desde o início do seu projeto. Dependendo do projeto, a ordem de exibição de seus ativos também pode ser um grande colaborador
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>Vídeo 2

**Criar métodos de experiência do usuário com um quadro completo holográfico** é importante entender o posicionamento de hologramas em um mundo físico. Lowe podemos falar sobre os diferentes métodos UX que ajudam os usuários a experiência hologramas backup feche ao mesmo tempo em que continua observando o ambiente maior de hologramas.

**Alinhamento de precisão** cenário para o Lowe, era essencial para a experiência tenha um alinhamento de precisão dos hologramas a cozinha física. Discutiremos técnicas ajuda a garantir uma experiência que convence os usuários que seu ambiente físico foi alterado.

**Compartilhado experiências holográfica** associa às é a principal maneira de que a experiência do Lowe é consumida. Uma pessoa pode alterar o balcão e a outra pessoa poderá ver as alterações. Chamamos esse "experiências compartilhadas".

**Interagindo com os clientes** designers do Lowe não estiver usando um HoloLens, mas que precisam ver o que os clientes estão vendo. Vamos mostrar como capturar o que o cliente está vendo em um aplicativo UWP.
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
