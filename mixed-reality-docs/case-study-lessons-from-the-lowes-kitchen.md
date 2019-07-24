---
title: Estudo de caso-lições da cozinha do Lowe
description: A equipe do HoloLens deseja compartilhar algumas das práticas recomendadas que foram derivadas do projeto HoloLens do Lowe.
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade do Windows Mixed, Lowe, HoloLens, cozinha, estudo de caso
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522347"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>Estudo de caso-lições da cozinha do Lowe

A equipe do HoloLens deseja compartilhar algumas das práticas recomendadas que foram derivadas do projeto HoloLens do Lowe. Veja a seguir um vídeo do HoloLens projetado do Lowe na palestra Satya de 2016 Ignite.
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Práticas recomendadas de HoloLens do Lowe

Os dois vídeos abrangem as práticas recomendadas que foram derivadas do piloto do HoloLens da Lowe que esteve em duas lojas de Lowe desde abril de 2016. Os principais tópicos são:
* Maximizar o desempenho de um dispositivo móvel
* Criar métodos UX com um quadro Holographic completo (2º palestra)
* Alinhamento de precisão (2ª palestra)
* Experiências de Holographic compartilhadas (2ª palestra)
* Interagindo com clientes (2º palestra)

## <a name="video-1"></a>Vídeo 1

**Maximizar o desempenho de um dispositivo móvel** O HoloLens é um dispositivo sem compartilhamento de Internet com todo o processamento em andamento no dispositivo. Isso requer uma plataforma móvel e requer uma mentalidade semelhante à criação de aplicativos móveis. A Microsoft recomenda que seu aplicativo do HoloLens Mantenha o 60FPS para fornecer uma experiência deliciosa para seus usuários. Ter baixas FPS pode resultar em hologramas instáveis.

Algumas das coisas mais importantes a serem examinadas ao desenvolver no HoloLens são a otimização de ativos/Decimation, usando sombreadores personalizados (disponíveis gratuitamente no [Kit de ferramentas do hololens](https://github.com/Microsoft/HoloToolkit-Unity)). Outra consideração importante é medir a taxa de quadros desde o início do seu projeto. Dependendo do projeto, a ordem de exibição de seus ativos também pode ser um grande colaborador
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>Vídeo 2

**Criar métodos UX com um quadro Holographic completo** É importante entender o posicionamento de hologramas em um mundo físico. Com o Lowe, falamos sobre diferentes métodos de UX que ajudam os usuários a experimentar os hologramas de perto e ainda ver o ambiente maior de hologramas.

**Alinhamento de precisão** Para o cenário do Lowe, era fundamental para a experiência ter o alinhamento da precisão dos hologramas com a cozinha física. Discutimos técnicas ajuda a garantir uma experiência que convença os usuários de que seu ambiente físico mudou.

**Experiências de Holographic** compartilhadas Os atestados são a principal maneira pela qual a experiência do Lowe é consumida. Uma pessoa pode alterar o balcão e a outra pessoa verá as alterações. Chamamos isso de "experiências compartilhadas".

**Interagindo com clientes** Os designers de Lowe não estão usando um HoloLens, mas precisam ver o que os clientes estão vendo. Mostramos como capturar o que o cliente está vendo em um aplicativo UWP.
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
