---
title: Processo de criação do ativo
description: Orientação sobre a criação de ativos para experiências de realidade misturada.
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: ativo, criação, processo, orçamento, polígonos, texturas, sombreadores, desempenho
ms.openlocfilehash: 513a9856ac35e4229cfb7bc8bcb92d9d6a152980
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692292"
---
# <a name="asset-creation-process"></a>Processo de criação do ativo

Windows Mixed Reality se baseia em décadas de investimento que a Microsoft fez no DirectX. Isso significa que todos os desenvolvedores a experiência e habilidades com a criação de 3D gráficos continuam a ser valiosa para HoloLens.

Os ativos que você cria para um projeto são fornecidos em várias formas e formulários. Eles podem ser compostos de uma série de texturas/imagens, áudio, vídeo, modelos 3D e animações. Não é possível começar cobrir todas as ferramentas que estão disponíveis para criar os diferentes tipos de ativos usados em um projeto. Para este artigo, nos concentraremos em métodos de criação de ativos 3D.

![Fluxo de conceito, criação, integração e iteração](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Fluxo de conceito, criação, integração e iteração*

## <a name="things-to-consider"></a>O que deve ser considerado

Quando examinar a experiência que você está tentando criar pense nisso como uma **orçamento** que você possa passar para tentar criar a melhor experiência. Não é necessariamente difícil limites no número de **polígonos** ou **tipos de materiais** usar em seus ativos, mas mais um conjunto orçado de vantagens e desvantagens.

Abaixo está um orçamento de exemplo para a sua experiência. Desempenho geralmente não é um ponto único de falha, mas morte por mil Cortes por-se.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Ativos</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> Memória</th>
</tr><tr>
<td> Polígonos</td><td> 0%</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> Texturas</td><td> 5%</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> Sombreadores</td><td> 15%</td><td> 35%</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Física</td><td> 5%</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> Iluminação em tempo real</td><td> 10%</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> Mídia (áudio/vídeo)</td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> Lógica do script</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> Sobrecarga geral</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>Total</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**Número total de ativos**
* Como muitos ativos estão ativos na cena?

**Complexidade de ativos**
* Quantos triângulos / polígonos?
* Quão complexo é o sombreador?

Desenvolvedores e artistas devem considerar os recursos do dispositivo e o mecanismo gráfico. Microsoft HoloLens tem todos os de computação e gráficos integrada no dispositivo. Ele compartilha os recursos que os desenvolvedores encontraria em uma plataforma móvel.

O processo de criação de ativos é o mesmo, independentemente se você estiver visando uma experiência para um [holográfico dispositivo ou um dispositivo de imersão](mixed-reality.md#the-mixed-reality-spectrum). A coisa principal a observar é a funcionalidade do dispositivo, conforme mencionado acima, bem como escala, pois você pode ver o mundo real na realidade misturada, que você desejará manter a escala correta com base na experiência. 

## <a name="authoring-assets"></a>Criação de ativos

Vamos começar com as maneiras de obter ativos para seu projeto:
1. Criação de ativos (ferramentas de criação e captura do objeto)
2. Compra de ativos (ativos em comprando on-line)
3. Portabilidade de ativos (levando ativos existentes)
4. Terceirização ativos (importando ativos de partes 3ª)

### <a name="creating-assets"></a>Criação de ativos

**Ferramentas de criação**<br>
Primeiro, você pode criar seus próprios ativos em um número de maneiras diferentes. Artistas 3D usam um número de aplicativos e ferramentas para criar modelos que consistem **malhas**, **texturas**, e **materiais**. Isso é salvo em um formato de arquivo que pode ser importado ou usado pelo mecanismo de elementos gráficos usado pelo aplicativo, tais como **. FBX** ou **. OBJ**. Qualquer ferramenta que gera um modelo que dá suporte a seu mecanismo de gráfico escolhido funcionará em **HoloLens**. Entre artistas 3D, muitos optar por usar [Autodesk Maya que por si só é capaz de usar o HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar os ativos da maneira como são criados. Se você quiser obter algo rápido você também pode usar [construtor 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) que vem com o Windows para exportar. OBJ para uso em seu aplicativo.

**Captura de objeto**<br>
Também há a opção para capturar objetos em 3D. Captura de objetos inanimados em 3D e editá-los com o software de criação de conteúdo digital é cada vez mais popular com o surgimento de impressão 3D. Usando o **Kinect 2** sensor e [construtor 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) você pode usar o recurso de captura para criar ativos de objetos do mundo real. Isso também é um [pacote de ferramentas](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) para fazer o mesmo com **photogrammetry** pelo processamento de um número de imagens para costurar junto e malha e texturas.

### <a name="purchasing-assets"></a>Compra de ativos

É outra excelente opção para ativos para a sua experiência de compra. Há uma tonelada de ativos disponíveis por meio de serviços, como o [Unity Asset Store](https://www.assetstore.unity3d.com/) ou [TurboSquid](http://www.turbosquid.com/) entre outros.

Quando você adquire os ativos de uma parte 3ª que sempre quiser verificar o seguinte:
* **O que é a contagem de poly?**
  * Ele se ajustar dentro do orçamento?
* **Há níveis de detalhe (LODs) para o modelo?**
  * Nível de detalhes de um modelo permitem que você dimensione os detalhes de um modelo para o desempenho.
* **O arquivo de origem está disponível?**
  * Normalmente, não estão incluídos no [Unity Asset Store](https://www.assetstore.unity3d.com/) , mas sempre incluído com serviços como [TurboSquid](http://www.turbosquid.com/).
  * Sem o arquivo de origem não será capaz de modificar o ativo.
  * Verifique se o arquivo de origem fornecido pode ser importado por suas ferramentas 3D.
* **Saber o que você esteja tirando**
  * As animações são fornecidas?
  * Certifique-se de verificar a lista de conteúdo do ativo que você vai adquirir.

### <a name="porting-assets"></a>Portabilidade de ativos

Em alguns casos, será entregue ativos existentes que foram originalmente criados para outros dispositivos e aplicativos diferentes. Na maioria dos casos, esses ativos podem ser convertidos para formatos compatíveis com o mecanismo gráfico do que seu aplicativo está usando.

Ao portar ativos para usar em seu aplicativo HoloLens, você desejará fazer o seguinte:
* **Você pode importar diretamente ou precisam ser convertidos para outro formato?** Verifique o formato que você está importando com o mecanismo de elementos gráficos que você está usando.
* **Se a conversão em um formato compatível é algo perdido?** Às vezes, os detalhes podem ser perdidos ou importando pode fazer com que os artefatos que precisam ser limpos em uma ferramenta de criação de 3D.
* **O que é os triângulos / contagem de polígonos para o ativo?** Com base no orçamento para o aplicativo você pode usar [Simplygon](https://www.simplygon.com/) ou ferramentas semelhantes para decimate (manual ou forma procedimental reduzir a contagem de poly) o ativo original para caber dentro do orçamento de aplicativos.

### <a name="outsourcing-assets"></a>Ativos de terceirização

Outra opção para projetos maiores que exigem mais ativos que sua equipe é equipado para criar é terceirizar a criação do ativo. O processo de terceirização envolve a localização do studio à direita ou a agência especializada em ativos de terceirização. Isso pode ser a opção mais cara, mas também ser a mais flexível em que você obtém.
* **Definir claramente o que está solicitando**
  * Forneça o máximo de detalhes possíveis
  * Frontal, lado e imagens do conceito de voltar
  * Ativo de mostrando de arte de referência no contexto
  * Escala do objeto (geralmente especificado em centímetros)
* **Forneça um orçamento**
  * Intervalo de contagem Poly
  * Número de texturas
  * Tipo de sombreador (para o Unity e HoloLens, você deve sempre padrão sombreadores móveis pela primeira vez)
* **Entender os custos**
  * Qual é a política de terceirização para solicitações de mudança?

Terceirização pode funcionar muito bem com base em sua linha do tempo de projetos, mas exige mais supervisão para garantir que você obtenha os ativos certos que na primeira vez que você precisa.
