---
title: MR espacial 230 - mapeamento espacial
description: Siga este passo a passo usando o Unity, o Visual Studio e o HoloLens para saber os detalhes dos conceitos de mapeamento espacial de codificação.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, mapeamento espacial, superfície reconstrução, malha
ms.openlocfilehash: 8d5715337ddd20e9868b18fdf0c63c704f584972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589757"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR Spatial 230: Mapeamento espacial

[Mapeamento espacial](spatial-mapping.md) combina o mundo real e o mundo virtual ensinando hologramas sobre o ambiente. Em MR espacial 230 (projeto Planetarium), você aprenderá como:

* Verificar os dados de ambiente e transferência do HoloLens para seu computador de desenvolvimento.
* Explore sombreadores e saiba como usá-las para visualizar seu espaço.
* Divida a malha de sala em planos simples usando o processamento de malha.
* Vá além das técnicas de posicionamento que aprendemos [MR Noções básicas de 101](holograms-101.md)e fornecer comentários sobre onde um holograma pode ser colocado no ambiente.
* Explore os efeitos de oclusão, portanto, quando seu holograma estiver atrás de um objeto do mundo real, você ainda poderá observá-la com a visão de raios-x!

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>MR Spatial 230: Mapeamento espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).
* Alguns basic C# capacidade de programação.
* Você deve ter concluído [MR Noções básicas de 101](holograms-101.md).
* Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
  * Se você ainda precisar de suporte do Unity 5.6, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).
  * Se você ainda precisar de suporte do Unity 5.5, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).
  * Se você ainda precisar de suporte de Unity 5.4, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).
* Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).

### <a name="notes"></a>Observações

* "Habilitar apenas meu código" no Visual Studio precisa ser desabilitado (*desmarcado*) em Ferramentas > Opções > depuração para usar pontos de interrupção em seu código.

## <a name="unity-setup"></a>Instalação do Unity

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* Inicie **Unity**.
* Selecione **New** para criar um novo projeto.
* Nomeie o projeto **Planetarium**.
* Verifique se que o **3D** configuração é selecionada.
* Clique em **criar projeto**.
* Depois que o Unity é iniciado, vá para **Editar > configurações do projeto > Player**.
* No **Inspector** do painel, localize e selecione o verde **Windows Store** ícone.
* Expandir **outras configurações**.
* No **renderização** seção, verifique os **suporte de realidade Virtual** opção.
* Verifique **Windows Holographic** aparece na lista de **SDKs de realidade Virtual**. Se não estiver, selecione a **+** botão na parte inferior da lista e escolha **Windows Holographic**.
* Expandir **configurações de publicação**.
* No **recursos** seção, verifique as seguintes configurações:
    * InternetClientServer
    * PrivateNetworkClientServer
    * Microfone
    * SpatialPerception
* Vá para **Editar > configurações do projeto > qualidade**
* No **Inspector** do painel, sob o ícone do Windows Store, selecione a seta suspensa preta sob a linha de 'Default' e altere a configuração padrão para **mais rápido**.
* Vá para **ativos > Importar pacote > pacote personalizado**.
* Navegue até a **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** pasta.
* Clique em **Planetarium.unitypackage**.
* Clique em **Abrir**.
* Uma **Importar pacote do Unity** janela deve ser exibida, clique no **importação** botão.
* Aguarde até que o Unity importar todos os ativos de que precisamos para concluir este projeto.
* No **hierarquia** do painel, exclua o **câmera principal**.
* No **projeto** painel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** pasta, localize o **câmera principal** objeto.
* Arraste e solte a **câmera principal** pré-fabricado para o **hierarquia** painel.
* No **hierarquia** do painel, exclua o **luz direcional** objeto.
* No **projeto** painel **hologramas** pasta, localize o **Cursor** objeto.
* Arrastar e soltar os **Cursor** pré-fabricado para o **hierarquia**.
* No **hierarquia** painel, selecione o **Cursor** objeto.
* No **Inspetor** do painel, clique no **camada** lista suspensa e selecione **camadas editar...** .
* Nome da **usuário camada 31** como "**SpatialMapping**".
* Salve a nova cena: **Arquivo > Salvar cena como...**
* Clique em **nova pasta** e nomeie a pasta **cenas**.
* Nomeie o arquivo "**Planetarium**" e salve-o na **cenas** pasta.

## <a name="chapter-1---scanning"></a>Capítulo 1 - varredura

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Objetivos**
* Saiba mais sobre o SurfaceObserver e como experiência seu impacto de configurações e o desempenho.
* Crie uma sala de experiência para coletar as malhas de sua sala de verificação.

**Instruções**
* No **projeto** painel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** pasta, localize o **SpatialMapping** pré-fabricado.
* Arrastar e soltar os **SpatialMapping** pré-fabricado para o **hierarquia** painel.

**Compilação e implantação (parte 1)**
* No Unity, selecione **arquivo > configurações de Build**.
* Clique em **adicionar cenas aberto** para adicionar o **Planetarium** cena para a compilação.
* Selecione **plataforma Universal do Windows** na **plataforma** lista e clique em **alternar plataforma**.
* Definir **SDK** à **10 Universal** e **tipo de Build de UWP** para **D3D**.
* Verifique **Unity C# projetos**.
* Clique em **Compilar**.
* Criar uma **nova pasta** chamado "App".
* Único clique a **aplicativo** pasta.
* Pressione a **Selecionar pasta** botão.
* Quando o Unity é feito criando, será exibida uma janela do Explorador de arquivos.
* Clique duas vezes no **aplicativo** pasta para abri-lo.
* Clique duas vezes em **Planetarium.sln** para carregar o projeto no Visual Studio.
* No Visual Studio, use a barra de ferramentas superior para alterar a configuração de **versão**.
* Alterar a plataforma **x86**.
* Clique na seta suspensa à direita de 'Local Machine' e selecione **computador remoto**.
* Insira [endereço IP do dispositivo](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) o endereço de campo e alterar o modo de autenticação **Universal (protocolo não criptografado)**.
* Clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.
* Assista a **saída** painel do Visual Studio para compilação e status de implantação.
* Depois que tiver implantado seu aplicativo, percorrer a sala. Você verá as superfícies ao redor cobertas por malhas de wireframe preto e branco.
* Examina seu ambiente. Certifique-se de examinar paredes, tetos e à base.

**Compilação e implantação (parte 2)**

Agora vamos explorar como mapeamento espacial pode afetar o desempenho.
* No Unity, selecione **Janela > Profiler**.
* Clique em **adicionar Profiler > GPU**.
* Clique em **Profiler Active Directory > <Enter IP>** .
* Insira o **endereço IP** de seu HoloLens.
* Clique em **Conectar**.
* Observe o número de milissegundos que leva para a GPU renderizar um quadro.
* Interrompa o aplicativo seja executado no dispositivo.
* Retorne ao Visual Studio e abra **SpatialMappingObserver.cs**. Você o encontrará na pasta HoloToolkit\SpatialMapping do projeto Assembly-CSharp (Windows Universal).
* Localizar o **Awake()** de função e adicione a seguinte linha de código: **TrianglesPerCubicMeter = 1200;**
* Reimplantar o projeto em seu dispositivo e, em seguida **reconectar-se o criador de perfil**. Observe a alteração no número de milissegundos para renderizar um quadro.
* Interrompa o aplicativo seja executado no dispositivo.

**Salvar e carregar no Unity**

Por fim, vamos salvar nosso malha sala e carregá-los no Unity.
* Retorne ao Visual Studio e remover as **TrianglesPerCubicMeter** que você adicionou na linha a **Awake()** função durante a seção anterior.
* Reimplante o projeto em seu dispositivo. Podemos agora deve ser executado com **500** triângulos por metro cúbico.
* Abra um navegador e insira no seu HoloLens IPAddress para navegar até a **Windows Device Portal**.
* Selecione o **exibição 3D** opção no painel esquerdo.
* Sob **reconstrução da superfície** selecionar a **atualização** botão.
* Assista como as áreas que examinados em seu HoloLens aparecem na janela de exibição.
* Para salvar sua verificação de espaço, pressione a **salvar** botão.
* Abra seu **baixa** pasta para encontrar o modelo salvo sala **SRMesh.obj**.
* Cópia **SRMesh.obj** para o **ativos** pasta do projeto do Unity.
* No Unity, selecione o **SpatialMapping** objeto de **hierarquia** painel.
* Localize o **observador de superfície do objeto (Script)** componente.
* Clique no círculo à direita do **sala modelo** propriedade.
* Localize e selecione o **SRMesh** do objeto e, em seguida, feche a janela.
* Verificar se o **modelo de sala** propriedade no **Inspetor** painel agora é definido como **SRMesh**.
* Pressione a **reproduzir** botão para entrar no modo de visualização do Unity.
* O componente SpatialMapping carregará as malhas do modelo de sala salvo para que você pode usá-los no Unity.
* Alterne para **cena** modo de exibição para ver todos os seu modelo de espaço exibido com o sombreador de wireframe.
* Pressione a **reproduzir** botão novamente para sair do modo de visualização.

**OBSERVAÇÃO:** Na próxima vez que você entra no modo de visualização no Unity, ele carregará a malha de sala salvos por padrão.

## <a name="chapter-2---visualization"></a>Capítulo 2 - visualização

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Objetivos**
* Conheça os fundamentos de sombreadores.
* Visualize o seu ambiente.

**Instruções**
* Do Unity **hierarquia** painel, selecione o **SpatialMapping** objeto.
* No **Inspector** do painel, localize a **Gerenciador de mapeamento espacial (Script)** componente.
* Clique no círculo à direita do **Material da superfície** propriedade.
* Localize e selecione o **BlueLinesOnWalls** material e feche a janela.
* No **Project** painel **sombreadores** pasta, clique duas vezes em **BlueLinesOnWalls** para abrir o sombreador no Visual Studio.
* Isso é um pixel simple (vértice para fragmentar) sombreador, que realiza as seguintes tarefas:
    1. Converte o local de um vértice espaço de mundo.
    2. Verifica que o vértice 's normal para determinar se um pixel é vertical.
    3. Define a cor do pixel para renderização.

**Criar e implantar**
* Retorne ao Unity e pressione **reproduzir** para entrar no modo de visualização.
* Linhas azuis serão renderizadas em todas as superfícies verticais da malha sala (o que automaticamente carregado de nossos dados de verificação salvos).
* Alterne para o **cena** tab para ajustar a exibição da sala e veja como a malha inteira espaço será exibida no Unity.
* No **Project** do painel, localize a **materiais** pasta e selecione o **BlueLinesOnWalls** material.
* Modificar algumas propriedades e ver como as alterações aparecem no editor do Unity.
    * No **Inspector** do painel, ajuste a **LineScale** valor para tornar as linhas aparecem mais espessa ou mais fina.
    * No **Inspector** do painel, ajuste a **LinesPerMeter** valor para alterar o número de linhas aparecem em cada parede.
* Clique em **reproduzir** novamente para sair do modo de visualização.
* Criar e implantar para o HoloLens e observar como o sombreador de renderização aparece em superfícies real.

Unity faz um excelente trabalho de visualização de materiais, mas é sempre uma boa ideia check-out de renderização no dispositivo.

## <a name="chapter-3---processing"></a>Capítulo 3 - processamento

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Objetivos**
* Aprenda técnicas para processar dados de mapeamento espacial para uso em seu aplicativo.
* Analise dados de mapeamento espacial para localizar planos e remover triângulos.
* Use planos para posicionamento holograma.

**Instruções**
* Do Unity **Project** painel, **hologramas** pasta, localize o **SpatialProcessing** objeto.
* Arrastar e soltar os **SpatialProcessing** do objeto para o **hierarquia** painel.

Pré-fabricado SpatialProcessing inclui componentes para processar os dados de mapeamento espacial. **SurfaceMeshesToPlanes.cs** encontrará e gerar planos com base nos dados de mapeamento espacial. Nós usaremos planos para representar paredes, andares e tetos em nosso aplicativo. Também inclui esse pré-fabricado **RemoveSurfaceVertices.cs** que pode remover os vértices da malha mapeamento espacial. Isso pode ser usado para criar buracos na malha, ou remover em excesso triângulos que não são mais necessários (porque os planos podem ser usados em vez disso).
* Do Unity **Project** painel, **hologramas** pasta, localize o **SpaceCollection** objeto.
* Arraste e solte a **SpaceCollection** do objeto para o **hierarquia** painel.
* No **hierarquia** painel, selecione o **SpatialProcessing** objeto.
* No **Inspector** do painel, localize a **reproduzir o Gerenciador de espaço (Script)** componente.
* Clique duas vezes em **PlaySpaceManager.cs** para abri-lo no Visual Studio.

PlaySpaceManager.cs contém código específico do aplicativo. Vamos adicionar funcionalidade a esse script para habilitar o seguinte comportamento:
1. Pare de coletar dados de mapeamento espacial, depois de exceder o limite de tempo de varredura (10 segundos).
2. Processe os dados de mapeamento espacial:
    1. Use SurfaceMeshesToPlanes para criar uma representação mais simples do mundo como planos (paredes, andares, tetos, etc.).
    2. Use RemoveSurfaceVertices para remover a superfície triângulos que caem dentro dos limites do plano.
3. Gerar uma coleção de hologramas no mundo e colocá-los em planos de parede e andar próxima ao usuário.

Concluir os exercícios de codificação marcados em PlaySpaceManager.cs ou substitua o script com a solução concluída abaixo:

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**Criar e implantar**
* Antes de implantar o HoloLens, pressione a **reproduzir** botão no Unity para entrar no modo de reprodução.
* Depois que a sala malha é carregada do arquivo, aguarde 10 segundos antes do início do processamento da malha de mapeamento espacial.
* Quando o processamento for concluído, os planos serão exibida para representar o chão, paredes, ceiling etc.
* Afinal de contas dos planos foram encontrados, você deverá ver um sistema solar aparecem em uma tabela de Chão de perto a câmera.
* Dois pôsteres devem aparecer no paredes perto da câmera muito. Alterne para o **cena** guia se você não pode vê-los na **jogo** modo.
* Pressione a **reproduzir** botão novamente para sair do modo de reprodução.
* Crie e implante como de costume para o HoloLens.
* Aguarde a verificação e processamento dos dados espaciais de mapeamento para ser concluída.
* Depois de ver planos, tente localizar o sistema solar e cartazes em seu mundo.

## <a name="chapter-4---placement"></a>Capítulo 4 - posicionamento

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Objetivos**
* Determine se um holograma serão ajustadas em uma superfície.
* Fornece comentários ao usuário quando um holograma pode/não couberem em uma superfície.

**Instruções**
* Do Unity **hierarquia** painel, selecione o **SpatialProcessing** objeto.
* No **Inspector** do painel, localize a **malhas para planos superfície (Script)** componente.
* Alterar o **desenhar planos** propriedade **nada** para limpar a seleção.
* Alterar o **desenhar planos** propriedade **parede**, de modo que apenas os planos de parede serão renderizados.
* No **projeto** painel **Scripts** pasta, clique duas vezes em **Placeable.cs** para abri-lo no Visual Studio.

O **Placeable** script já está anexado ao cartazes e caixa de projeção que são criados após a conclusão da localização do plano. Tudo que precisamos fazer é remover os comentários de código, e esse script irá obter o seguinte:
1. Determine se um holograma serão ajustadas em uma superfície de raycasting do centro e quatro cantos do cubo delimitadora.
2. Verificar a superfície normal para determinar se ele é suave para o holograma de liberação esperar na.
3. Processa um cubo delimitadora em torno de holograma para mostrar o tamanho real ao que está sendo colocado.
4. Converta uma sombra em/atrás do holograma para mostrar onde ele será colocado na parede/andar.
5. Renderize a sombra como vermelho, se o holograma não pode ser colocado na superfície ou verde, se possível.
6. O holograma para alinhar com o tipo de superfície (horizontal ou vertical) que tem afinidade para re-Oriente.
7. Sem problemas coloca o holograma na superfície de selecionado para evitar saltar ou comportamento de encaixe.

Remova todo o código no exercício codificação abaixo ou usar essa solução concluída em **Placeable.cs**:

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**Criar e implantar**
* Como antes, compile o projeto e implantar para o HoloLens.
* Aguarde a verificação e processamento dos dados espaciais de mapeamento para ser concluída.
* Quando você vir o sistema solar, mantenha o foco em caixa projeção abaixo e execute um gesto de select movê-lo. Enquanto a caixa de projeção é selecionada, um cubo delimitadora ficará visível em torno da caixa de projeção.
* Mova head para mantenha o foco em um local diferente na sala. A caixa de projeção deve siga seu foco. Quando a sombra abaixo da caixa de projeção fica vermelha, você não pode colocar o holograma em que são exibidos. Quando a sombra abaixo da caixa de projeção fica verde, você pode colocar o holograma executando gesto selecione outro.
* Localize e selecione um dos cartazes holográfico uma parede para movê-lo para um novo local. Observe que você não pode colocar o cartaz na base ou ceiling e que ele permaneça orientado corretamente para cada parede move ao redor.

## <a name="chapter-5---occlusion"></a>Capítulo 5 - oclusão

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Objetivos**
* Determine se um holograma é obstruído pela malha mapeamento espacial.
* Aplicar as técnicas de oclusão diferentes para alcançar um divertido em vigor.

**Instruções**

Primeiro, vamos permitir que a malha de mapeamento espacial para occlude outras hologramas sem occluding do mundo real:
* No **hierarquia** painel, selecione o **SpatialProcessing** objeto.
* No **Inspector** do painel, localize a **reproduzir o Gerenciador de espaço (Script)** componente.
* Clique no círculo à direita do **Material secundário** propriedade.
* Localize e selecione o **oclusão** material e feche a janela.

Em seguida, vamos adicionar um comportamento especial a Terra, para que ele tenha um realce azul sempre que ele se torna obstruído pelo outro holograma (como o sol) ou pela malha mapeamento espacial:
* No **Project** painel, o **hologramas** pasta, expanda o **SolarSystem** objeto.
* Clique em **Terra**.
* No **Inspetor** painel, localizar o material da Terra (componente inferior).
* No **suspensa sombreador**, altere o sombreador **personalizado > OcclusionRim**. Isso será renderizado um realce azul ao redor de terra sempre que ele é obstruído por outro objeto.

Por fim, vamos habilitar um efeito de visão de raios-x para planetas em nosso sistema solar. Precisaremos editar **PlanetOcclusion.cs** (encontrado na pasta Scripts\SolarSystem) para alcançar o seguinte:
1. Determine se um planeta é obstruído pela camada de SpatialMapping (sala malhas e planos).
2. Mostre a representação de wireframe de um planeta sempre que ele é obstruído pela camada de SpatialMapping.
3. Oculte a representação de wireframe de um planeta quando ele não está bloqueado pela camada de SpatialMapping.

Siga o exercício de codificação em PlanetOcclusion.cs ou usar a solução a seguir:

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**Criar e implantar**
* Crie e implante o aplicativo para o HoloLens, como de costume.
* Aguarde a verificação e processamento dos dados espaciais de mapeamento para ser concluída (você deve ver linhas azuis na paredes).
* Localize e selecione a caixa de projeção do sistema solar e, em seguida, defina a caixa ao lado de uma parede ou atrás de um contador.
* Você pode exibir oclusão básica esconder atrás superfícies emparelhar a caixa de pôster ou projeção.
* Procure a Terra, deve haver um efeito de realce azul sempre que ele fica atrás de outro holograma ou superfície.
* Assista como planetas mover por trás de parede ou outras superfícies na sala. Agora você tem a visão de raios-x e pode ver seus esqueletos de wireframe!

## <a name="the-end"></a>Fim

Parabéns! Agora você concluiu **MR de 230 espacial: Mapeamento espacial**.
* Você sabe como fazer a varredura de seus dados de ambiente e carga mapeamento espacial para o Unity.
* Você compreender os fundamentos de sombreadores e como os materiais podem ser usados para visualizar novamente o mundo.
* Você aprendeu sobre novas técnicas de processamento para localizar planos e removendo os triângulos de uma malha.
* Você conseguiu mover e coloque hologramas em superfícies que fazia sentido.
* Você apresentou técnicas diferentes de oclusão e aproveitar a potência da visão de raios-x!
