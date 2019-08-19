---
title: Crie modelos 3D para uso na página inicial
description: Requisitos de ativos e diretrizes de criação para modelos 3D a serem usados na página inicial do Windows Mixed Realm tanto em fones de HoloLens quanto em headsets de imersão (VR).
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, modelagem, diretrizes de modelagem, requisitos de ativos, diretrizes de criação, iniciador, iniciador 3D, textura, materiais, complexidade, triângulos, malha, polígonos, semicontagem, limites
ms.openlocfilehash: 73af40cf2915742cab612625c8243a36ee74d748
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692287"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Crie modelos 3D para uso na página inicial

O [Windows Mixed Reality Home](navigating-the-windows-mixed-reality-home.md) é o ponto de partida onde os usuários vão antes de iniciar os aplicativos. Você pode projetar seu aplicativo para os headsets de realidade mista do Windows para aproveitar um [modelo 3D como um inicializador de aplicativo](implementing-3d-app-launchers.md) e permitir que [links de 3D Deep sejam colocados na página inicial do Windows Mixed Realm](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) de dentro de seu aplicativo. Este artigo descreve as diretrizes para a criação de modelos 3D compatíveis com a página inicial do Windows Mixed Reality.

## <a name="asset-requirements-overview"></a>Visão geral dos requisitos de ativo
Ao criar modelos 3D para a realidade mista do Windows, há alguns requisitos que todos os ativos devem atender: 
1. [Exportando](#exporting-models) - os ativos devem ser entregues no formato de arquivo. glb (glTF binário)
2. [Modelagem](#modeling-guidelines) -os ativos devem ser inferiores a 10.000 triângulos, não têm mais de 64 nós e 32 submalhas por LOD
3. Os [materiais](#material-guidelines) -texturas não podem ser maiores que 4096 x 4096 e o menor mapa MIP não deve ser maior que 4 em qualquer uma das dimensões
4. [Animação](#animation-guidelines) -as animações não podem ter mais de 20 minutos a 30 FPS (36.000 quadros chave) e devem conter < = 8192 vértices de destino de Morph
5. [Otimizando](#optimizations) -os ativos devem ser otimizados usando o [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases). Isso é **necessário nas versões do sistema operacional windows < = 1709** e recomendado nas versões do sistema operacional Windows > = 1803

O restante deste artigo inclui uma visão geral detalhada desses requisitos, bem como diretrizes adicionais para garantir que seus modelos funcionem bem com a página inicial do Windows Mixed Reality. 

## <a name="detailed-guidance"></a>Diretrizes detalhadas

### <a name="exporting-models"></a>Exportando modelos

A Home real do Windows Mixed espera que os ativos 3D sejam entregues usando o formato de arquivo. glb com imagens inseridas e dados binários. Glb é a versão binária do formato glTF, que é um padrão aberto isento de royalties para entrega de ativos 3D mantido pelo grupo Khronos. À medida que o glTF evolui como um padrão do setor para conteúdo interoperável 3D, portanto, o suporte da Microsoft para o formato entre aplicativos e experiências do Windows. Se você não tiver criado um ativo glTF antes de encontrar uma [lista de exportadores e conversores com suporte](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) na página GitHub do grupo de trabalho do glTF.  

### <a name="modeling-guidelines"></a>Diretrizes de modelagem

O Windows espera que os ativos sejam gerados usando as diretrizes de modelagem a seguir para garantir a compatibilidade com a experiência de residência de realidade misturada. Ao modelar em seu programa de sua escolha, tenha em mente as seguintes recomendações e limitações:
1. O eixo para cima deve ser definido como "Y".
2. O ativo deve enfrentar "encaminhar" em direção ao eixo Z positivo.
3. Todos os ativos devem ser criados no plano de chão na origem da cena (0, 0, 0)
4. As unidades de trabalho devem ser definidas como medidores e ativos para que os ativos possam ser criados em escala mundial
5. Todas as malhas não precisam ser combinadas, mas recomendadas se você estiver direcionando dispositivos com restrição de recursos
6. Todas as malhas devem compartilhar 1 material, com apenas 1 conjunto de texturas sendo usado para todo o ativo
7. UVs deve ser disposta em uma organização quadrada no espaço de 0-1. Evite texturas de divisão, embora elas sejam permitidas.
8. Não há suporte para UVs
9. Não há suporte para materiais duplos de lado

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Contagens de triângulos e níveis de detalhes (LODs)

A página inicial do Windows Mixed Reality não oferece suporte a modelos com mais de 10.000 triângulos. É recomendável que você triangulaia suas malhas antes de exportar para garantir que elas não excedam essa contagem. O Windows MR também dá suporte a LODs (níveis adicionais de geometria de detalhes) para garantir uma experiência de alto desempenho e de alta qualidade. [O WindowsMRAssetConverter o](https://github.com/Microsoft/glTF-Toolkit/releases) ajudará a combinar 3 versões do seu modelo em um único modelo. glb. O Windows determina qual LOD será exibido com base na quantidade de espaço de tela que o modelo está ocupando. Há suporte apenas para três níveis de LOD com as seguintes contagens de triângulo recomendadas:
<br>

|  Nível de LOD  |  Contagem de triângulos recomendada  |  Contagem de triângulo máxima | 
|------|------|------|
|  LOD 0 |  10.000 |  10.000 | 
|  LOD 1 |  5\.000  |  10.000 | 
|  LOD 2 |  2\.500  |  10.000 | 

### <a name="node-counts-and-submesh-limits"></a>Contagens de nós e limites de submalha
A página inicial do Windows Mixed Reality não oferece suporte a modelos com mais de 64 nós ou 32 submalhas por LOD. Os nós são um conceito na [especificação glTF](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) que definem os objetos na cena. As submalhas são definidas na matriz de [primitivos](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) na malha no objeto. 

|  Recurso |  Descrição  |  Máximo com suporte | Documentação |
|------|------|------|------|
|  Nós |  Objetos na cena glTF |  64 por LOD | [Aqui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submalhas |  Soma de primitivos em todas as malhas |  32 por LOD | [Aqui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Diretrizes do material

As texturas devem ser preparadas usando um fluxo de trabalho de commãos de metal de PBR Comece criando um conjunto completo de texturas, incluindo albedo, normal, oclusão, metal e áspero. O Windows Mixed Reality dá suporte a texturas com resoluções até 4096x4096, mas recomendamos que você crie em 512x512. Além disso, as texturas devem ser criadas em resoluções em múltiplos de 4, pois esse é um requisito para o formato de compactação aplicado às texturas nas etapas de exportação descritas abaixo. Finalmente, quando os mapas MIP gerating ou uma textura, o MIP mais baixo deve ser um máximo de 4x4.
<br>

|  Tamanho de textura recomendado  |  Tamanho máximo da textura | MIP mais baixo
|----|----|----|
|  512x512  |  4096x4096 | 4x4 máx.|

### <a name="albedo-base-color-map"></a>Mapa de albedo (cor de base)

Cor bruta sem informações de iluminação. Esse mapa também contém as informações de reflexão e difusa para o metal (branco no mapa metálico) e as superfícies do isolador (preto no mapa metálico), respectivamente.

### <a name="normal"></a>Normal

Mapa normal de espaço tangente

### <a name="roughness-map"></a>Mapa de irregularidade

Descreve a microsuperfície do objeto. O White 1,0 é um esboço preto 0,0 é suave. Esse mapa dá ao ativo o maior caractere, pois ele realmente descreve a superfície, por exemplo, arranhões, impressões digitais, manchas, sujeira, etc.

### <a name="ambient-occlusion-map"></a>Mapa de oclusão de ambiente

Mapa de escala de valor que representa áreas de luz obstruído que bloqueiam reflexos

### <a name="metallic-map"></a>Mapa metálico

Informa ao sombreador se algo está metal ou não. Metal bruto = 1,0 branco não metal = 0,0 preto. Pode haver valores cinzas em transição que indicam algo que cobre o metal bruto, como sujeira, mas, em geral, esse mapa deve ser apenas preto e branco.

## <a name="optimizations"></a>Otimizações

O Windows Mixed Reality Home oferece uma série de otimizações sobre a especificação glTF básica definida usando extensões personalizadas. Essas otimizações são necessárias em versões do Windows < = 1709 e recomendadas em versões mais recentes do Windows. Você pode otimizar facilmente qualquer modelo glTF 2,0 usando o [conversor de ativos do Windows Mixed Reality disponível no GitHub](https://github.com/Microsoft/glTF-Toolkit/releases). Essa ferramenta executará a embalagem e as otimizações de textura corretas, conforme especificado abaixo. Para uso geral, é recomendável usar o WindowsMRAssetConverter, mas se você precisar de mais controle sobre a experiência e quiser criar seu próprio pipeline otimização, poderá consultar a especificação detalhada abaixo.  

### <a name="materials"></a>Materiais

Para melhorar o tempo de carregamento de ativos em ambientes de realidade misturados, o Windows MR dá suporte à renderização de texturas DDS compactadas, de acordo com o esquema de embalagem de textura definido nesta seção As texturas DDS são referenciadas usando a [extensão MSFT_texture_dds](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds). É altamente recomendável compactar texturas. 

#### <a name="hololens"></a>HoloLens

As experiências de realidade misturada com base em HoloLens esperam que as texturas sejam empacotadas usando uma configuração de textura 2 usando a seguinte especificação de embalagem:
<br>

|  Propriedade glTF  |  Textura  |  Esquema de embalagem | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Vermelho (R), verde (G), azul (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  Normal (RG), áspero (B), metal (A) | 


Ao compactar as texturas DDS, espera-se a seguinte compressão em cada mapa:
<br>

|  Textura  |  Compactação esperada | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Headsets de imersão (VR)

As experiências de realidade mista do Windows com base em PC para headsets de imersão (VR) esperam que as texturas sejam empacotadas usando uma configuração de 3 texturas usando a seguinte especificação de embalagem:

##### <a name="windows-os--1803"></a>> Do sistema operacional Windows = 1803

<br>

|  Propriedade glTF  |  Textura  |  Esquema de embalagem | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Vermelho (R), verde (G), azul (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Oclusão (R), áspero (G), metálico (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Ao compactar as texturas DDS, espera-se a seguinte compressão em cada mapa:
<br>

|  Textura  |  Compactação esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>< Do sistema operacional Windows = 1709
<br>

|  Propriedade glTF  |  Textura  |  Esquema de embalagem | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Vermelho (R), verde (G), azul (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Áspero (R), metal (G), oclusão (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Ao compactar as texturas DDS, espera-se a seguinte compressão em cada mapa:
<br>

|  Textura  |  Compactação esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>Adicionando LODs de malha

O Windows MR usa o nó Geometry LODs para renderizar modelos 3D em diferentes níveis de detalhes, dependendo da cobertura da tela. Embora esse recurso não seja necessário tecnicamente, é altamente recomendável para todos os ativos. Atualmente, o Windows dá suporte a três níveis de detalhes. O LOD padrão é 0, que representa a qualidade mais alta. Outros LODs são numerados em sequência, por exemplo, 1, 2 e ficam progressivamente inferiores em qualidade. O [conversor de ativos de realidade do Windows Mixed](https://github.com/Microsoft/glTF-Toolkit/releases) dá suporte à geração de ativos que atendem a essa especificação de Lod, aceitando vários modelos de glTF e mesclando-os em um único ativo com níveis LOD válidos. A tabela a seguir descreve a ordem LOD esperada e os destinos do triângulo:
<br>

|  Nível de LOD  |  Contagem de triângulos recomendada  |  Contagem de triângulo máxima | 
|-------|-------|-------|
|  LOD 0 |  10.000 |  10.000 | 
|  LOD 1 |  5\.000  |  10.000 | 
|  LOD 2 |  2\.500  |  10.000 | 

Ao usar LODs, sempre especifique 3 níveis de LOD. O LODs ausente fará com que o modelo não seja renderizado inesperadamente, pois o sistema LOD muda para o nível de LOD ausente. o glTF 2,0 atualmente não dá suporte a LODs como parte da especificação principal. O LODs deve, portanto, ser definido usando a [extensão MSFT_LOD](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).

### <a name="screen-coverage"></a>Cobertura de tela

LODs são exibidos no Windows Mixed Reality com base em um sistema controlado pelo valor de cobertura de tela definido em cada LOD. Os objetos que estão consumindo uma parte maior do espaço da tela são exibidos em um nível de LOD mais alto. A cobertura de tela não faz parte da especificação Core glTF 2,0 e deve ser especificada usando MSFT_ScreenCoverage na seção "extras" da [extensão MSFT_lod](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).
<br>

|  Nível de LOD  |  Intervalo recomendado  |  Intervalo padrão | 
|-------|-------|-------|
|  LOD 0  |  100%-50% |  5 | 
|  LOD 1 |  Menos de 50%-20%  |  0,2 | 
|  LOD 2 |  Menos de 20% a 1%  |  0,01 | 
|  LOD 4  |  Menos de 1%  |  - | 

## <a name="animation-guidelines"></a>Diretrizes de animação

> [!NOTE]
> Esse recurso foi adicionado como parte da [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md). Em versões mais antigas do Windows, essas animações não serão reproduzidas, no entanto, elas ainda serão carregadas se forem criadas de acordo com as diretrizes neste artigo.  

A página de realidade misturada dá suporte a objetos glTF animados em headsets de HoloLens e de imersão (VR). Se você quiser disparar animações em seu modelo, precisará usar a extensão de mapa de animação no formato glTF. Essa extensão permite disparar animações no modelo glTF com base na presença dos usuários no mundo, por exemplo, disparar uma animação quando o usuário estiver próximo ao objeto ou enquanto estiver olhando para ele. Se você glTF objeto tem animações, mas não define gatilhos, as animações não serão reproduzidas. A seção a seguir descreve um fluxo de trabalho para adicionar esses gatilhos a qualquer objeto glTF animado.

### <a name="tools"></a>Ferramentas
Primeiro, baixe as ferramentas a seguir se você ainda não as tiver. Essas ferramentas facilitarão a abertura de qualquer modelo glTF, a visualização, a realização de alterações e o salvamento de back como glTF ou. glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [Ferramentas de glTF para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Abrindo e visualizando o modelo
Comece abrindo o modelo glTF no VSCode arrastando o arquivo. glTF para a janela do editor. Observe que, se você tiver um. glb em vez de um arquivo. glTF, poderá importá-lo no VSCode usando o suplemento de ferramentas do glTF que você baixou. Acesse "Exibir-> paleta de comandos" e comece digitando "glTF" na paleta de comandos e selecione "glTF: Importar do glb "que exibirá um seletor de arquivos para você importar um. glb com. 

Depois de abrir o modelo do glTF, você deverá ver o JSON na janela do editor. Observe que você também pode visualizar o modelo em um visualizador 3D ao vivo usando o clicando com o botão direito do mouse no nome do arquivo e selecionando o "glTF: Visualizar modelo 3D "atalho de comando no menu de clique com o botão direito do mouse. 

### <a name="adding-the-triggers"></a>Adicionando os gatilhos
Os gatilhos de animação são adicionados ao modelo glTF JSON usando a extensão de mapa de animação. A extensão de mapa de animação está documentada publicamente [aqui no GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (Observação: ESTA É UMA EXTENSÃO DE RASCUNHO). Para adicionar a extensão ao modelo, basta rolar até o final do arquivo glTF no editor e adicionar o bloco "extensionsUsed" e "Extensions" ao arquivo, caso ainda não existam. Na seção "extensionsUsed", você adicionará uma referência à extensão "EXT_animation_map" e no bloco "Extensions", adicionará seus mapeamentos às animações no modelo.

Conforme observado [na especificação](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) , você define o que dispara a animação usando a cadeia de caracteres "semântica" em uma lista de "animações", que é uma matriz de índices de animação. No exemplo abaixo, especificamos a animação a ser reproduzida enquanto o usuário está nuvens no objeto:

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
A semântica de gatilhos de animação a seguir tem suporte na página inicial do Windows Mixed Reality.  
* "SEMPRE": Loop constante de uma animação
* "MANTIDO": Em loop durante toda a duração de um objeto ser capturado.
* "OLHAR": Em loop enquanto um objeto está sendo examinado
* "PROXIMIDADE": Em loop enquanto um visualizador está próximo a um objeto
* "APONTANDO": Em loop enquanto um usuário está apontando para um objeto

### <a name="saving-and-exporting"></a>Salvando e exportando
Depois de fazer as alterações no modelo glTF, você poderá salvá-las diretamente como glTF ou clicar com o botão direito do mouse no nome do arquivo no editor e selecionar "glTF: Exportar para GLB (arquivo binário) "em vez disso, exportar um. glb. 

### <a name="restrictions"></a>Restrições
As animações não podem ter mais de 20 minutos e não podem conter mais de 36.000 quadros-chave (20 minutos a 30 FPS). Além disso, ao usar animações baseadas em destino Morph não exceda 8192 vértices de destino de Morph ou menos. Exceder essas contagens demoraremá que o ativo animado não terá suporte na página inicial do Windows Mixed Reality. 

|Recurso|Máximo|
|-----|-----|
|Duração|20 minutos|
|Quadros-chave|36.000| 
|Vértices de destino de Morph|8192|

## <a name="gltf-implementation-notes"></a>notas de implementação do glTF
O Windows Sr não dá suporte à inversão de geometria usando escalas negativas. A geometria com escalas negativas provavelmente resultará em artefatos visuais.

O ativo glTF deve apontar para a cena padrão usando o atributo Scene a ser renderizado pelo Windows Sr. Além disso, o carregador do Windows Sr glTF antes da [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md) **requer** acessadores:
* Deve ter valores mínimo e máximo.
* O tipo escalar deve ser ComponentType UNSIGNED_SHORT (5123) ou UNSIGNED_INT (5125).
* O tipo VEC2 e VEC3 deve ser o ComponentType FLOAT (5126).

As seguintes propriedades de material são usadas na especificação Core glTF 2,0, mas não são necessárias:
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture: Deve apontar para uma textura armazenada em DDS.
* emissiveTexture: Deve apontar para uma textura armazenada em DDS.
* emissiveFactor
* alphamode

As seguintes propriedades de material são ignoradas da especificação principal:
* Todos os UVs
* metalRoughnessTexture: Em vez disso, deve usar a embalagem de textura otimizada da Microsoft definida abaixo
* normalTexture: Em vez disso, deve usar a embalagem de textura otimizada da Microsoft definida abaixo
* normalScale
* occlusionTexture: Em vez disso, deve usar a embalagem de textura otimizada da Microsoft definida abaixo
* occlusionStrength

O Windows Sr não dá suporte a linhas e pontos de modo primitivo. 

Há suporte apenas para um único atributo de vértice UV.

## <a name="additional-resources"></a>Recursos adicionais
* [exportadores e conversores glTF](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [Kit de ferramentas glTF](https://github.com/Microsoft/glTF-Toolkit)
* [Especificação do glTF 2,0](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Especificação de extensão do Microsoft glTF LOD](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [Especificação de extensões de empacotamento de textura do PC Mixed Reality](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [Especificação de extensões de empacotamento de textura da realidade misturada do HoloLens](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Especificação de extensões glTF do Microsoft DDS Textures](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Consulte também

* [Implementar inicializadores de aplicativos 3D (aplicativos UWP)](implementing-3d-app-launchers.md)
* [Implementar inicializadores de aplicativos 3D (aplicativos Win32)](implementing-3d-app-launchers-win32.md)
* [Como navegar na página inicial do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
