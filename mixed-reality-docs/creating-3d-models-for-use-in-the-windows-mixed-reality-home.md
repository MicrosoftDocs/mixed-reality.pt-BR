---
title: Criar modelos 3D para uso em casa
description: Requisitos de ativo e criação de diretrizes para modelos 3D a ser usado no Windows Mixed Reality home no HoloLens e fones imersivos em exposição (VR).
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Limites de modelagem 3D, orientação, requisitos de ativo, criação de diretrizes, iniciador, iniciador 3D, texturas, materiais, complexidade, triângulos, malha, polígonos, polycount, de modelagem
ms.openlocfilehash: 209a92a8e7070ca23bcb9402d8716f3f91747a96
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589347"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Criar modelos 3D para uso em casa

O [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) é o ponto de partida em que os usuários cheguem antes de iniciar aplicativos. Você pode projetar seu aplicativo para headsets Windows Mixed Reality aproveitar uma [modelo 3D como um inicializador de aplicativos](implementing-3d-app-launchers.md) e para permitir [3D links profundos sejam colocados em que o Windows Mixed Reality doméstica](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) de dentro de seu aplicativo. Este artigo descreve as diretrizes para criar modelos 3D compatível com o Windows Mixed Reality inicial.

## <a name="asset-requirements-overview"></a>Visão geral dos requisitos de ativo
Ao criar modelos 3D para Windows Mixed Reality, há alguns requisitos que devem atender a todos os ativos: 
1. [Exportando](#exporting-models) -ativos devem ser entregues no formato de arquivo .glb (glTF binário)
2. [Modelagem](#modeling-guidelines) -ativos deve ser triângulos de menos de 10 k, ter não mais do que 64 nós e 32 submeshes por LOD
3. [Materiais](#material-guidelines) - texturas não podem ser maiores do que 4096x4096 e o mapa mip menor deve ser maior que 4 em qualquer dimensão
4. [Animação](#animation-guidelines) -animações não podem ter mais de 20 minutos a 30 FPS (quadros-36.000 chave) e deve conter < = 8192 vértices de destino morph
5. [Otimizando](#optimizations) -ativos devem ser otimizados usando o [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases). Isso é **necessário em versões do sistema operacional Windows < = 1709** e recomendado em versões do sistema operacional do Windows > = 1803

O restante deste artigo inclui uma visão geral detalhada desses requisitos, bem como diretrizes adicionais para garantir que seus modelos funcionam bem com o Windows Mixed Reality inicial. 

## <a name="detailed-guidance"></a>Orientação detalhada

## <a name="exporting-models"></a>Exportando modelos

O Windows Mixed Reality doméstica espera ativos 3D para ser fornecidas usando o formato de arquivo .glb com imagens inseridas e dados binários. Glb é a versão binária do formato glTF que é um royalty de padrão aberto gratuito para entrega de ativos 3D mantido pelo grupo Khronos. À medida que glTF evolui como um padrão do setor para conteúdo 3D interoperável assim será suporte da Microsoft para o formato em aplicativos do Windows e experiências. Se você não tiver criado um ativo de glTF antes que você pode encontrar uma [lista de Exportadores com suporte e conversores](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) na página do github glTF trabalho grupo.  

## <a name="modeling-guidelines"></a>Diretrizes de modelagem

Windows espera ativos a ser gerado usando as seguintes diretrizes de modelagem para garantir a compatibilidade com a experiência inicial de realidade misturada. Durante a modelagem em seu programa de sua escolha tenha em mente as seguintes recomendações e limitações:
1. O eixo vertical deve ser definido como "Y".
2. O ativo deve enfrentar "forward" na direção do eixo positivo Z.
3. Todos os ativos devem ser criados no plano de zero a origem da cena (0, 0,0)
4. Unidades de trabalho devem ser definidas como medidores e ativos, para que os ativos podem ser criados em escala mundial
5. Todas as malhas não precisam ser combinados, mas é recomendável se você estiver direcionando os dispositivos de restrição de recursos
6. Todas as malhas devem compartilhar o material de 1, com apenas 1 textura definida que está sendo usada para o ativo de inteiro
7. UVs devem ser dispostos em uma organização quadrada em de 0 a 1 espaço. Evite texturas de lado a lado, embora eles têm permissão.
8. Não há suporte para multi-UVs
9. Não há suporte para materiais de lado e Double

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Contagens de triângulo e níveis de detalhe (LODs)

O Windows Mixed Reality inicial não oferece suporte a modelos com mais de 10.000 triângulos. É recomendável que você triangular seu malhas antes de importá-los para garantir que eles não excedam Essa contagem. Windows MR também dá suporte a níveis de geometria opcional de detalhe (LODs) para garantir uma experiência de alta qualidade e de alto desempenho. [O WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) ajudará você a combinar 3 versões do seu modelo em um modelo único .glb. Windows determina quais LOD para exibir com base na quantidade de espaço na tela, que o modelo está ocupando. Níveis LOD apenas 3 são compatíveis com o seguinte recomendado contagens de triângulo:
<br>

|  Nível LOD  |  Contagem de triângulo recomendada  |  Contagem máxima de triângulo | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>Limites de contagens de nó e submalha realçada
O Windows Mixed Reality inicial não oferece suporte a modelos com mais de 64 nós ou 32 submeshes por LOD. Nós são um conceito a [glTF especificação](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) que definem os objetos na cena. Submeshes são definidos na matriz de [primitivos](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) da malha no objeto. 

|  Recurso |  Descrição  |  Máximo com suporte | Documentação |
|------|------|------|------|
|  Nós |  Objetos em que a cena glTF |  64 por LOD | [Aqui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  Soma dos primitivos de todas as malhas |  32 por LOD | [Aqui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Diretrizes de material

Texturas devem ser preparadas usando um fluxo de trabalho de metal Aspereza PBR. Comece criando um conjunto completo de texturas incluindo Albedo, Normal, oclusão, metálica e Aspereza. Realidade mista do Windows dá suporte a texturas com resoluções até 4096x4096, mas recomendamos autor em 512 x 512. Além disso, as texturas devem ser criadas em resoluções em múltiplos de 4 como este é um requisito para o formato de compactação aplicado às texturas nas etapas de exportação descritas abaixo. Por fim, quando os mapas mip gerating ou uma textura de mip mais baixo deve ser um máximo de 4 x 4.
<br>

|  Tamanho da textura recomendado  |  Tamanho máximo de textura | Mip mais baixo
|----|----|----|
|  512x512  |  4096x4096 | máximo de 4 x 4|

### <a name="albedo-base-color-map"></a>Mapa de albedo (cor de base)

Cor bruto com nenhuma informação de iluminação. Este mapa também contém a reflexão e difusa informações para metal (branco no mapa metálico) e superfícies isolador (preto no mapa metálico), respectivamente.

### <a name="normal"></a>Normal

Mapa de Normal do espaço tangente

### <a name="roughness-map"></a>Mapa de Aspereza

Descreve o microsurface do objeto. 1.0 em branco é aproximada preto 0,0 é suave. Este mapa fornece o ativo, a maioria dos caracteres como ele realmente descreve a superfície, por exemplo, aborda as impressões digitais, manchas, sujeira etc.

### <a name="ambient-occlusion-map"></a>Mapa de oclusão de ambiente

Mapa de escala do valor ilustrando as áreas de luz obstruído que bloqueia os reflexos

### <a name="metallic-map"></a>Mapa metálico

Informa o sombreador se algo é o sistema operacional ou não. Metal bruto = 1.0 metal não branco = 0,0 preto. Pode haver valores cinzas transitional que indicam algo que abrangem a metal bruta como sujeira, mas em geral esse mapa deve ser somente branco e preto.

## <a name="optimizations"></a>otimizações

Windows Mixed Reality doméstica oferece uma série de otimizações sobre a especificação de glTF core definidos usando as extensões personalizadas. Essas otimizações são necessários em versões do Windows < = 1709 e recomendado em versões mais recentes do Windows. Você pode facilmente otimizar a qualquer modelo glTF 2.0 usando o [misto realidade ativo conversor Windows disponível no GitHub](https://github.com/Microsoft/glTF-Toolkit/releases). Essa ferramenta realizará a textura correta de empacotamento e otimizações conforme especificado abaixo. Para uso geral é recomendável usar o WindowsMRAssetConverter, mas se você precisa de mais controle sobre a experiência e gostaria de criar seu próprio pipeline de otimização, em seguida, você pode consultar a especificação detalhada abaixo.  

### <a name="materials"></a>Materiais

Para melhorar o tempo em ambientes de realidade misturada MR do Windows de carregamento de ativos dá suporte à renderização de texturas compactadas de DDS compactadas de acordo com a textura de remessa esquema definido nesta seção. Texturas DDS são referenciadas usando o [MSFT_texture_dds extensão](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds). É altamente recomendável compactar as texturas. 

#### <a name="hololens"></a>HoloLens

Experiências de realidade misturada com base em HoloLens esperam texturas para ser empacotado usando uma configuração de 2 textura usando a seguinte especificação de remessa:
<br>

|  glTF propriedade  |  Textura  |  Esquema de remessa | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  R (vermelho), G (verde), azul (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  Normal (RG), (B), de Aspereza metálica (A) | 


Ao compactar as texturas DDS a compactação a seguir é esperada em cada mapa:
<br>

|  Textura  |  Compactação esperada | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Fones imersivos em exposição (VR)

Experiências de realidade mista do Windows baseados em PC para fones imersivos em exposição (VR) esperam texturas para ser empacotado usando uma configuração de 3 textura usando a seguinte especificação de remessa:

##### <a name="windows-os--1803"></a>Windows OS >= 1803

<br>

|  glTF propriedade  |  Textura  |  Esquema de remessa | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  R (vermelho), G (verde), azul (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Occlusion (R) Aspereza (G), metálica (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Ao compactar as texturas DDS a compactação a seguir é esperada em cada mapa:
<br>

|  Textura  |  Compactação esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS <= 1709
<br>

|  glTF propriedade  |  Textura  |  Esquema de remessa | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  R (vermelho), G (verde), azul (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Roughness (R) metálica (G) e oclusão (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Ao compactar as texturas DDS a compactação a seguir é esperada em cada mapa:
<br>

|  Textura  |  Compactação esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>Adicionando malha LODs

MR do Windows usa o nó de geometria LODs para processar modelos 3D em diferentes níveis de detalhe, dependendo da cobertura de tela. Embora esse recurso não seja tecnicamente necessário, é altamente recomendável para todos os ativos. Atualmente, o Windows dá suporte a 3 níveis de detalhe. O padrão LOD é 0, que representa a melhor qualidade. Outros LODs são numerados sequencialmente, por exemplo, 1, 2 e get progressivamente mais baixo na qualidade. O [conversor de ativos de realidade mista do Windows](https://github.com/Microsoft/glTF-Toolkit/releases) dá suporte à geração de ativos que atendem a essa especificação LOD aceitando vários modelos de glTF e mesclá-las em um único ativo com níveis LOD válidos. A tabela a seguir descreve as metas de ordenação e triângulo LOD esperadas:
<br>

|  Nível LOD  |  Contagem de triângulo recomendada  |  Contagem máxima de triângulo | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

Ao usar LODs sempre Especifica 3 níveis LOD. Faltando LODs fará com que o modelo não renderizar inesperadamente, como os sistema-alternâncias de LOD para o nível LOD ausente. glTF 2.0 não oferece suporte atualmente LODs como parte da especificação de núcleo. LODs, portanto, devem ser definidas usando o [extensão MSFT_LOD](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).

### <a name="screen-coverage"></a>Cobertura de tela

LODs são exibidos em realidade mista do Windows com base em um sistema fosse controlado pelo valor de cobertura da tela, definido em cada LOD. Objetos que estão atualmente consumindo uma porção maior do que o espaço de tela são exibidos em um nível mais alto de LOD. Cobertura de tela não é uma parte da especificação de glTF 2.0 core e deve ser especificada usando MSFT_ScreenCoverage na seção "extras" a [MSFT_lod extensão](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).
<br>

|  Nível LOD  |  Intervalo recomendado  |  Intervalo padrão | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  .5 | 
|  LOD 1 |  Menos de 50% a 20%  |  .2 | 
|  LOD 2 |  Menos de 20% a 1%  |  .01 | 
|  LOD 4  |  Abaixo de % 1  |  - | 

## <a name="animation-guidelines"></a>Diretrizes de animação

> [!NOTE]
> Esse recurso foi adicionado como parte da [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md). Em versões anteriores do Windows, essas animações não serão executada, no entanto, eles ainda carregará se criados de acordo com as diretrizes neste artigo.  

A página inicial de realidade misturada dá suporte a objetos animados glTF em HoloLens e fones imersivos em exposição (VR). Se você deseja disparar animações em seu modelo, você precisará usar a extensão de mapa de animação no formato de glTF. Essa extensão permite disparar animações no modelo glTF com base na presença de usuários no mundo, por exemplo, disparar uma animação quando o usuário está perto o objeto ou enquanto estiverem visualizando-lo. Se o objeto do glTF tem animações, mas não define gatilhos as animações não serão executadas novamente. A seção a seguir descreve um fluxo de trabalho para adicionar esses gatilhos para qualquer objeto glTF animado.

### <a name="tools"></a>Ferramentas
Primeiro, baixe as ferramentas a seguir se você ainda não tivê-los. Essas ferramentas tornará mais fácil abrir qualquer modelo glTF, visualizá-lo, fazer alterações e salvar-como glTF ou .glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [glTF ferramentas para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Abrindo e visualizando o modelo
Comece abrindo o modelo glTF no VSCode, arrastando o arquivo .glTF na janela do editor. Observe que, se você tiver um .glb em vez de um arquivo .glTF você pode importá-lo para VSCode através do suplemento do ferramentas glTF que você baixou. Vá para "Exibir -> Paleta de comandos" e, em seguida, comece a digitar "glTF" na paleta de comandos e selecione "glTF: Importar do glb"que será exibida para que você importe um .glb com um seletor de arquivos. 

Depois de abrir seu modelo glTF, você deve ver o JSON na janela do editor. Observe que também é possível visualizar o modelo em um visualizador 3D em tempo real usando o botão direito do mouse clicando no nome do arquivo e selecionando o "glTF: Visualizar o modelo 3D"o atalho de comando de menu de atalho. 

### <a name="adding-the-triggers"></a>Adicionando os gatilhos
Gatilhos de animação são adicionados ao modelo glTF JSON usando a extensão de mapa de animação. A extensão de mapa de animação está documentada publicamente [aqui no GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (Observação: ESSA É UMA EXTENSÃO DE RASCUNHO). Para adicionar a extensão a rolagem de apenas seu modelo até o final do arquivo glTF no editor e adicionar o bloco "extensionsUsed" e "extensões" ao seu arquivo, se ainda não existirem. Na seção "extensionsUsed", você adicionará uma referência para a extensão "EXT_animation_map" e o bloco "extensões", você adicionará seus mapeamentos para as animações no modelo.

Conforme observado [nas especificações de](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) você definir o que dispara a animação usando a cadeia de caracteres "semântica" em uma lista de "animações" que é uma matriz de índices de animação. No exemplo a seguir, especificamos a animação reproduzir quando o usuário é Observação no objeto:

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
A seguinte semântica de gatilhos de animação é compatíveis com o Windows Mixed Reality inicial.  
* "SEMPRE": Loop constantemente uma animação
* "MANTIDAS": Em loop durante toda a duração é pegou um objeto.
* "OLHARES": Em loop enquanto um objeto está sendo examinado
* "PROXIMIDADE": Em loop enquanto um visualizador está perto de um objeto
* "APONTANDO": Em loop enquanto um usuário está apontando para um objeto

### <a name="saving-and-exporting"></a>Salvando e exportando
Uma vez você fez as alterações ao seu modelo de glTF, você pode salvá-lo diretamente como glTF ou com o botão direito no nome do arquivo no editor e selecione "glTF: Exportar a GLB (arquivo binário) "em vez disso, exportar um .glb. 

### <a name="restrictions"></a>Restrições
Animações não podem ter mais de 20 minutos e não podem conter mais de 36.000 quadros-chave (20 minutos a 30 QPS). Além ao usar o destino de morph com base em animações não exceder 8192 vértices de destino morph ou menos. Excedendo esses demorarem será de contagem ativo não terão mais suporte no ambiente doméstico Windows Mixed Reality animado. 

|Recurso|Máximo|
|-----|-----|
|Duração|20 minutos|
|Quadros-chave|36,000| 
|Morph vértices de destino|8192|

## <a name="gltf-implementation-notes"></a>Notas de implementação glTF
MR do Windows não oferece suporte a inversão de geometry usando escalas negativas. Geometria com escalas negativo provavelmente resultará em artefatos visuais.

O ativo glTF deve apontar para a cena padrão usando o atributo de cena para ser processado pelo MR do Windows. Além disso, o carregador de glTF MR do Windows antes do [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md) **requer** acessadores:
* Deve ter valores mínimo e máximo.
* Tipo de ESCALAR deve ser componentType UNSIGNED_SHORT (5123) ou UNSIGNED_INT (5125).
* Tipo VEC2 e VEC3 devem ser componentType FLOAT (5126).

As propriedades de material a seguir são usadas na especificação de glTF 2.0 core, mas não obrigatórios:
* baseColorFactor metallicFactor, roughnessFactor
* baseColorTexture: Deve apontar para uma textura armazenada em dds.
* emissiveTexture: Deve apontar para uma textura armazenada em dds.
* emissiveFactor
* alphaMode

As seguintes propriedades de material são ignoradas da especificação principal:
* Todos os Multi-UVs
* metalRoughnessTexture: Em vez disso, deve usar o empacotamento de textura Microsoft otimizado definido abaixo
* normalTexture: Em vez disso, deve usar o empacotamento de textura Microsoft otimizado definido abaixo
* normalScale
* occlusionTexture: Em vez disso, deve usar o empacotamento de textura Microsoft otimizado definido abaixo
* occlusionStrength

MR do Windows não oferece suporte pontos e linhas de modo primitivo. 

Há suporte para apenas um único atributo de vértice de UV.

## <a name="additional-resources"></a>Recursos adicionais
* [glTF Exportadores e conversores de](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 especificação](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF LOD especificação de extensão](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [PC misturadas realidade especificação de extensões de empacotamento de textura](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens misturadas realidade especificação de extensões de empacotamento de textura](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Especificação de extensões do Microsoft DDS texturas glTF](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Consulte também

* [Implementar iniciadores de aplicativo 3D (aplicativos UWP)](implementing-3d-app-launchers.md)
* [Implementar iniciadores de aplicativo 3D (aplicativos Win32)](implementing-3d-app-launchers-win32.md)
* [Navegando o Windows Mixed Reality inicial](navigating-the-windows-mixed-reality-home.md)
