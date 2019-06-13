---
title: Adicionar ambientes domésticos personalizados
description: Além dos ambientes iniciais do Windows Mixed Reality que fornecemos, você pode experimentar com a criação e usar seu próprio.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, realidade mista, realidade Virtual, VR, MR, Home, ambientes personalizados, lugares, casa cliff, skyloft, usuário, criar
ms.openlocfilehash: d0cdb878f1994cb5f898f06b98d74dee3dd4fdf1
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024535"
---
# <a name="add-custom-home-environments"></a>Adicionar ambientes domésticos personalizados

>[!NOTE]
>Esse é um recurso experimental. Experimente e divirta-se com ele, mas não se surpreenda se tudo o que não funciona muito bem conforme o esperado. Estamos avaliando a viabilidade desse recurso e interesse em usá-lo, portanto, informe-nos sobre sua experiência (e quaisquer erros que você encontrou) na [fóruns para desenvolvedores](https://forums.hololens.com/categories/custom-home-environments).

Começando com o [atualização do Windows 10 de abril de 2018](#release-notes-april-2018.md), habilitamos um recurso experimental que permite adicionar ambientes personalizados para seletor de locais (no menu Iniciar) para usar como o [Windows Mixed Reality home](#navigating-the-windows-mixed-reality-home.md). Realidade mista do Windows tem dois ambientes padrão, Cliff House e Skyloft, que você pode escolher como sua página inicial. Criar ambientes personalizados permite que você expanda essa lista com suas próprias criações. Estamos fazendo isso disponível em um estado inicial para avaliar o interesse de criadores e desenvolvedores, veja quais tipos de mundos você cria e entender como trabalhar com ferramentas de criação de diferentes.

Ao usar um ambiente personalizado, você observará que teleporting, interagir com os aplicativos e a colocação hologramas funcionam exatamente como faria no Cliff House e Skyloft. Você pode navegar na web em um cenário de fantasia ou preencher uma cidade futuristas com hologramas - as possibilidades são infinitas!

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
        <td>Ambientes domésticos personalizados</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>Tentativa de um ambiente de exemplo

Criamos um ambiente de exemplo que mostra algumas das possibilidades criativas de ambientes domésticos personalizados. Siga estas etapas para experimentá-lo:
1. [Baixe o nosso ambiente de fantasia ilha de exemplo](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link aponta para um executável auto-extraível).

    ![Ambiente de exemplo da ilha de fantasia](images/FantasyLand.jpg)<br>
    *Ambiente de exemplo da ilha de fantasia*<br>

2. Execute o **Fantasy_Island.exe** arquivo que você acabou de baixar.

    > [!NOTE]
    > Ao tentar executar um arquivo .exe baixado da web (como este), você pode encontrar um pop-up "Windows protegido seu PC". Para executar Fantasy_Island.exe desse pop-up, selecione **saber** e, em seguida **executar mesmo assim**. Essa configuração de segurança destina-se a proteger você contra o download de arquivos que você não deseja confiar, isso apenas Escolha esta opção quando você confia na origem do arquivo.

3. Abra **Explorador de arquivos** e navegue até a pasta ambientes colando o seguinte na barra de endereços: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.
4. Copie o ambiente de exemplo que você baixou para essa pasta.
5. Reinicie **misto realidade Portal**. Isso atualizará a lista de ambientes no seletor de locais.
6. Coloque em fone de ouvido. Quando você estiver usando a página inicial, abra o **menu Iniciar** usando o Windows botão seu controlador.
7. Selecione o **casas** ícone acima da lista de aplicativos fixados para escolher um ambiente doméstico.
8. Você encontrará o ambiente de fantasia ilha que você baixou na sua lista de locais. Selecione **ilha de fantasia** para inserir seu novo ambiente de página inicial personalizado!

## <a name="creating-your-own-custom-environment"></a>Criar seu próprio ambiente personalizado

Além de usar nossos ambientes de exemplo, você pode exportar seus próprios ambientes personalizados usando seu software de edição de 3D favorito. 

### <a name="modeling-guidelines"></a>Diretrizes de modelagem

Ao modelar seu ambiente, lembre-se as recomendações a seguir. Isso ajudará a garantir que o cria o usuário na orientação correta em um mundo em believably tamanho:

1. Os usuários irá gerar 0, 0,0 Center caso seu local desejado spawn em torno da origem.
2. Unidades de trabalho devem ser definidas para os medidores, de modo que os ativos podem ser criados em escala mundial.
3. O eixo vertical deve ser definido como "Y".
4. O ativo deve enfrentar "forward" na direção do eixo positivo Z.
5. Todas as malhas não precisam ser combinados, mas é recomendável se você estiver direcionando os dispositivos com recursos limitados.

### <a name="exporting-your-environment"></a>Exportação de seu ambiente

Realidade mista do Windows se baseia em binário glTF (.glb) como o formato de entrega de ativo para ambientes. glTF é um royalty livre padrão aberto para entrega de ativos 3D mantido pelo grupo Khronos. À medida que evolui glTF como um padrão do setor para conteúdo 3D interoperável, assim será suporte da Microsoft para o formato em aplicativos do Windows e experiências.

A primeira etapa na exportação ativos a ser usado como ambientes domésticos personalizados é gerar um modelo de glTF 2.0. O grupo de trabalho glTF mantém uma [lista de Exportadores com suporte e conversores](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) para criar um modelo de glTF 2.0. Para começar, use um dos programas listados nesta página para criar e exportar um modelo de glTF 2.0, ou converter um modelo existente usando um dos conversores com suporte.

Além disso, fazer check-out [este artigo útil](https://www.khronos.org/blog/art-pipeline-for-gltf) que fornece uma visão geral de um fluxo de trabalho de arte para Exportando modelos glTF do Blender e o 3DS Max diretamente. 

### <a name="environment-limits"></a>Limites de ambiente

Todos os ambientes devem ser < 256 MB. Ambientes de maiores que 256 MB falhará carregar e fallback para um mundo vazio com apenas o skybox padrão ao redor do usuário. Mantenha esse limite de tamanho de arquivo em mente ao criar seus modelos. Além disso, se você planeja otimizar seu ambiente usando o WindowsMRAssetConverter conforme descrito abaixo, estar ciente de que o tamanho da textura aumentará conforme o otimizador cria as texturas que têm um tamanho de arquivo maior, mas são carregadas mais rapidamente. 

### <a name="optimizing-your-environment"></a>Otimizando seu ambiente

Realidade mista do Windows oferece suporte a uma série de otimizações opcionais que reduz significativamente o tempo de carregamento de seus ambientes. Isso pode ser especialmente importante para ambientes com muitas texturas, pois eles, às vezes, atingirão o tempo limite durante o carregamento. Em geral, é recomendável que essa etapa para todos os ativos, no entanto, com poucas ou de baixa resolução texturas em ambientes menores não exigirá sempre-lo. 

Para facilitar esse processo, criamos a [misto realidade ativo conversor Windows (disponível no GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) para executar suas otimizações. Essa ferramenta usa um conjunto de utilitários disponíveis no Kit de ferramentas do Microsoft glTF para otimizar qualquer glTF 2.0 padrão ou .glb executando uma remessa de textura adicionais, compactação e a resolução reduções no dimensionamento. 

O conversor atualmente dá suporte a um número de sinalizadores para ajustar o comportamento exato das otimizações. Recomendamos a execução com os sinalizadores a seguir para obter melhores resultados:

Flag|Valor (es) recomendada|Descrição
---|---|---
-max-texture-size|1024 ou 2048| Ajustar isso para melhorar a qualidade das texturas, o padrão é 512 x 512. Observe que um valor maior irá afetar significativamente o tamanho do arquivo do ambiente tenha até o limite de 256 mb em mente
versão mínima|1803|Ambientes personalizados têm suporte apenas em versões do windows > = 1803. Esse sinalizador removerá as texturas para versões mais antigas e reduzir o tamanho do arquivo do ativo final

Por exemplo:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>Seu ambiente de teste

Uma vez que seu ambiente .glb final, você está pronto para testá-lo no fone de ouvido. Iniciar na etapa 2 a ["Tentativa de um ambiente de exemplo"](#trying-a-sample-environment) seção para usar seu ambiente personalizado como a base de realidade misturada. 

## <a name="feedback"></a>Privacidade Jurídica

Enquanto estamos avaliando este recurso experimental, estamos interessados em aprender como você está usando ambientes personalizados, qualquer bug que você pode encontrar, e como você deseja que o recurso. Compartilhe seus comentários todo e para criar e usar ambientes domésticos personalizados na [fóruns para desenvolvedores](https://forums.hololens.com/categories/custom-home-environments).

## <a name="troubleshooting-and-tips"></a>Dicas e solução de problemas

### <a name="how-do-i-change-the-name-of-the-environment"></a>Como altero o nome do ambiente?

O nome do arquivo na pasta ambientes será usado no seletor de locais. Para alterar o nome do seu ambiente simplesmente renomear o ambiente de nome de arquivo e, em seguida, reinicie o Portal de realidade mista.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>Como remover ambientes personalizados do meu selecionador de locais?

Para remover um ambiente personalizado, abra a pasta de ambientes no seu PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) e excluir o ambiente. Após o reinício do Portal de realidade misturada, esse ambiente não aparecerá mais no seletor de locais. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>Como padrão para o meu favorito ambiente personalizado?

No momento, você não pode alterar o ambiente padrão. Toda vez que reiniciar o Portal de realidade misturada, você será retornado para o ambiente Cliff House. 

### <a name="i-spawn-into-a-blank-space"></a>Gerar a em um espaço em branco

Windows Mixed Reality [não dá suporte a ambientes que excedam 256 mb](#environment-limits). Quando um ambiente excede esse limite, você será levado a caixa vazia céu sem modelo.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>Demora muito tempo para carregar meu ambiente

Você pode adicionar otimizações opcionais ao seu ambiente para torná-lo são carregadas mais rapidamente. Ver ["Otimizando seu ambiente"](#optimizing-your-environment) para obter detalhes.

### <a name="the-scale-of-my-environment-is-incorrect"></a>A escala do meu ambiente está incorreta

Windows Mixed Reality converte glTF unidades de 1 metro ao carregar ambientes. Se seu ambiente carrega uma escala inesperada, verifique novamente seu exportador para garantir que você esteja modelando em uma escala de 1 metro. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>O local de geração no meu ambiente está incorreto

O local de spawn padrão está localizado em 0, 0,0 no ambiente. Seu não no momento, é possível personalizar esse local, portanto, você deve modificar o ponto de geração por meio da exportação de seu ambiente com a origem posicionada no ponto desejado spawn.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>O áudio não parece correto no ambiente

Quando você cria seu ambiente personalizado, ele usará uma simulação de renderização acústica que não coincide com o espaço físico que você criou. Pode parecer e podem ser provenientes de direções erradas de som muffled. 

## <a name="see-also"></a>Consulte também
* [Windows misturadas realidade conversor de ativo (no GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)

