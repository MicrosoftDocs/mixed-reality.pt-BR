---
title: Sr espacial 230-mapeamento espacial
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes dos conceitos espaciais de mapeamento.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, mapeamento espacial, reconstrução de superfície, malha
ms.openlocfilehash: cf4a2dd3e5eb74c0aaf849442e5f5e404d7cb661
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434575"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR espacial 230: mapeamento espacial

O [mapeamento espacial](spatial-mapping.md) combina o mundo real e o mundo virtual juntos ao ensinar hologramas sobre o ambiente. No Sr espacial 230 (projeto Planetarium), aprenderemos a:

* Examine o ambiente e transfira dados do HoloLens para seu computador de desenvolvimento.
* Explore os sombreadores e saiba como usá-los para visualizar seu espaço.
* Divida a malha Room em planos simples usando o processamento de malha.
* Vá além das técnicas de posicionamento que aprendemos no [Sr basics 101](holograms-101.md)e forneça comentários sobre onde um holograma pode ser colocado no ambiente.
* Explore os efeitos do oclusão, portanto, quando o holograma estiver atrás de um objeto do mundo real, você ainda poderá vê-lo com a visão x-ray!

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>MR espacial 230: mapeamento espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md).
* Alguma capacidade C# básica de programação.
* Você deve ter concluído o [Sr noções básicas 101](holograms-101.md).
* Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) exigidos pelo projeto. Requer o Unity 2017,2 ou posterior.
  * Se você ainda precisar de suporte do Unity 5,6, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).
  * Se você ainda precisar de suporte do Unity 5,5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).
  * Se você ainda precisar de suporte do Unity 5,4, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).
* Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).

### <a name="notes"></a>Observações

* "Habilitar Apenas Meu Código" no Visual Studio precisa ser desabilitado (*desmarcado*) em Ferramentas > Opções > depuração para acessar pontos de interrupção em seu código.

## <a name="unity-setup"></a>Configuração do Unity

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* Inicie o **Unity**.
* Selecione **novo** para criar um novo projeto.
* Nomeie o projeto **Planetarium**.
* Verifique se a configuração **3D** está selecionada.
* Clique em **Criar Projeto**.
* Depois que o Unity for iniciado, vá para **Editar configurações do projeto > > Player**.
* No painel **Inspetor** , localize e selecione o ícone verde da **Windows Store** .
* Expanda **outras configurações**.
* Na seção **renderização** , verifique a opção **suporte à realidade virtual** .
* Verifique se o **Windows Holographic** aparece na lista de **SDKs de realidade virtual**. Caso contrário, selecione o botão **+** na parte inferior da lista e escolha **Windows Holographic**.
* Expanda **configurações de publicação**.
* Na seção **recursos** , verifique as seguintes configurações:
    * InternetClientServer
    * PrivateNetworkClientServer
    * Microfone
    * SpatialPerception
* Vá para **Editar configurações de projeto > > qualidade**
* No painel **Inspetor** , sob o ícone Windows Store, selecione a seta suspensa preta na linha ' padrão ' e altere a configuração padrão para **muito baixa**.
* Acesse **ativos > importar pacote > pacote personalizado**.
* Navegue até a pasta **. ..\holographicacademy-holograms-230-SpatialMapping\Starting** .
* Clique em **Planetarium. unitypackage**.
* Clique em **Abrir**.
* Uma janela **Importar pacote do Unity** deve aparecer, clique no botão **importar** .
* Aguarde até que o Unity importe todos os ativos para os quais precisaremos concluir este projeto.
* No painel **hierarquia** , exclua a **câmera principal**.
* No painel **projeto** , pasta **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** , localize o objeto **principal da câmera** .
* Arraste e solte o pré-fabricado da **câmera principal** no painel **hierarquia** .
* No painel **hierarquia** , exclua o objeto de **luz direcional** .
* No painel **projeto** , pasta **hologramas** , localize o objeto **cursor** .
* Arraste & solte o **cursor** pré-fabricado na **hierarquia**.
* No painel **hierarquia** , selecione o objeto **cursor** .
* No painel **Inspetor** , clique na lista suspensa **camada** e selecione **Editar camadas...** .
* Nome a **camada de usuário 31** como "**SpatialMapping**".
* Salve a nova cena: **arquivo > salvar cena como...**
* Clique em **nova pasta** e nomeie a pasta **cenas**.
* Nomeie o arquivo como "**Planetarium**" e salve-o na pasta de **cenas** .

## <a name="chapter-1---scanning"></a>Capítulo 1-verificando

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Seus**

* Saiba mais sobre o SurfaceObserver e como suas configurações impactam a experiência e o desempenho.
* Crie uma experiência de verificação de sala para coletar as malhas da sua sala.

**Sobre**

* Na pasta **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** do painel de **projeto** , localize o **SpatialMapping** pré-fabricado.
* Arraste & soltar o pré-fabricado **SpatialMapping** no painel **hierarquia** .

**Compilar e implantar (parte 1)**

* No Unity, selecione **arquivo > configurações de Build**.
* Clique em **Adicionar abrir cenas** para adicionar a cena **Planetarium** à compilação.
* Selecione **plataforma universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.
* Defina o **SDK** para o **tipo de compilação** **Universal 10** e UWP como **D3D**.
* Verifique **os C# projetos do Unity**.
* Clique em **Compilar**.
* Crie uma **nova pasta** chamada "app".
* Clique uma vez na pasta do **aplicativo** .
* Pressione o botão **Selecionar pasta** .
* Quando o Unity terminar a compilação, uma janela Explorador de arquivos será exibida.
* Clique duas vezes na pasta do **aplicativo** para abri-la.
* Clique duas vezes em **Planetarium. sln** para carregar o projeto no Visual Studio.
* No Visual Studio, use a barra de ferramentas superior para alterar a configuração a ser **liberada**.
* Altere a plataforma para **x86**.
* Clique na seta suspensa à direita de ' máquina local ' e selecione **máquina remota**.
* Insira [o endereço IP do dispositivo](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) no campo endereço e altere o modo de autenticação para **Universal (protocolo não criptografado)** .
* Clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.
* Assista ao painel de **saída** no Visual Studio para o status de compilação e implantação.
* Depois que seu aplicativo for implantado, percorra a sala. Você verá as superfícies ao redor cobertas por malhas de wireframe preto e branco.
* Examine seu ambiente. Certifique-se de examinar as paredes, os tetos e os andares.

**Compilar e implantar (parte 2)**

Agora vamos explorar como o mapeamento espacial pode afetar o desempenho.

* No Unity, selecione **Window > Profiler**.
* Clique em **Adicionar criador de perfil > GPU**.
* Clique em **Active Profiler > <Enter IP>** .
* Insira o **endereço IP** do seu HoloLens.
* Clique em **Conectar**.
* Observe o número de milissegundos que leva para a GPU renderizar um quadro.
* Impedir que o aplicativo seja executado no dispositivo.
* Retorne ao Visual Studio e abra **SpatialMappingObserver.cs**. Você o encontrará na pasta HoloToolkit\SpatialMapping do projeto assembly-CSharp (universal do Windows).
* Localize a função **ativo ()** e adicione a seguinte linha de código: **TrianglesPerCubicMeter = 1200;**
* Implante novamente o projeto em seu dispositivo e **reconecte o criador de perfil**. Observe a alteração no número de milissegundos para renderizar um quadro.
* Impedir que o aplicativo seja executado no dispositivo.

**Salvar e carregar no Unity**

Por fim, vamos salvar nossa malha Room e carregá-la no Unity.

* Retorne ao Visual Studio e remova a linha **TrianglesPerCubicMeter** que você adicionou na função de **ativo ()** durante a seção anterior.
* Reimplante o projeto em seu dispositivo. Agora devemos estar executando com **500** triângulos por medidor cúbico.
* Abra um navegador e insira o endereço IP do seu HoloLens para navegar até o **portal do dispositivo Windows**.
* Selecione a opção **exibição 3D** no painel esquerdo.
* Em **reconstrução da superfície** , selecione o botão **Atualizar** .
* Observe como as áreas que você examinou em seu HoloLens aparecem na janela de exibição.
* Para salvar sua verificação de sala, pressione o botão **salvar** .
* Abra a pasta **downloads** para localizar o modelo de sala salvo **SRMesh. obj**.
* Copie **SRMesh. obj** para a pasta **ativos** do seu projeto do Unity.
* No Unity, selecione o objeto **SpatialMapping** no painel **hierarquia** .
* Localize o componente **observador de superfície de objeto (script)** .
* Clique no círculo à direita da propriedade de **modelo de sala** .
* Localize e selecione o objeto **SRMesh** e feche a janela.
* Verifique se a propriedade **modelo de sala** no painel **Inspetor** agora está definida como **SRMesh**.
* Pressione o botão **reproduzir** para inserir o modo de visualização do Unity.
* O componente SpatialMapping carregará as malhas do modelo de sala salvo para que você possa usá-las no Unity.
* Alterne para a exibição de **cena** para ver todo o modelo de sala exibido com o sombreador delineado.
* Pressione o botão **reproduzir** novamente para sair do modo de visualização.

**Observação:** Na próxima vez que você inserir o modo de visualização no Unity, ele carregará a malha de sala salva por padrão.

## <a name="chapter-2---visualization"></a>Capítulo 2 – visualização

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Seus**

* Aprenda os fundamentos dos sombreadores.
* Visualize seu ambiente.

**Sobre**

* No painel **hierarquia** do Unity, selecione o objeto **SpatialMapping** .
* No painel **Inspetor** , localize o componente do **Gerenciador de mapeamento espacial (script)** .
* Clique no círculo à direita da propriedade **material da superfície** .
* Localize e selecione o material de **BlueLinesOnWalls** e feche a janela.
* Na pasta **sombreadores** do painel de **projeto** , clique duas vezes em **BlueLinesOnWalls** para abrir o sombreador no Visual Studio.
* Este é um sombreador simples de pixel (vértice para fragmento), que realiza as seguintes tarefas:
    1. Converte o local de um vértice no espaço do mundo.
    2. Verifica o normal do vértice para determinar se um pixel é vertical.
    3. Define a cor do pixel para renderização.

**Compilar e implantar**

* Retorne ao Unity e pressione **reproduzir** para entrar no modo de visualização.
* As linhas azuis serão renderizadas em todas as superfícies verticais da malha Room (que são carregadas automaticamente de nossos dados de verificação salvos).
* Alterne para a guia **cena** para ajustar sua exibição da sala e ver como a malha de sala inteira aparece no Unity.
* No painel **projeto** , localize a pasta **materiais** e selecione o material **BlueLinesOnWalls** .
* Modifique algumas propriedades e veja como as alterações aparecem no editor do Unity.
    * No painel **Inspetor** , ajuste o valor **LineScale** para que as linhas pareçam mais espessas ou mais finas.
    * No painel **Inspetor** , ajuste o valor **LinesPerMeter** para alterar a quantidade de linhas exibidas em cada parede.
* Clique em **reproduzir** novamente para sair do modo de visualização.
* Crie e implante no HoloLens e observe como a renderização do sombreador aparece em superfícies reais.

O Unity faz um ótimo trabalho de visualização de materiais, mas é sempre uma boa ideia fazer check-out do processamento no dispositivo.

## <a name="chapter-3---processing"></a>Capítulo 3-processando

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Seus**

* Aprenda técnicas para processar dados de mapeamento espacial para uso em seu aplicativo.
* Analise os dados de mapeamento espacial para localizar planos e remover triângulos.
* Use planos para posicionamento de holograma.

**Sobre**

* Na pasta painel de **projeto** do Unity, **hologramas** , localize o objeto **SpatialProcessing** .
* Arraste & solte o objeto **SpatialProcessing** no painel **hierarquia** .

O SpatialProcessing pré-fabricado inclui componentes para processar os dados de mapeamento espacial. **SurfaceMeshesToPlanes.cs** encontrará e gerará planos com base nos dados de mapeamento espacial. Usaremos planos em nosso aplicativo para representar paredes, andares e tetos. Esse pré-fabricado também inclui **RemoveSurfaceVertices.cs** que pode remover vértices da malha de mapeamento espacial. Isso pode ser usado para criar buracos na malha ou para remover triângulos excedentes que não são mais necessários (porque os planos podem ser usados em vez disso).

* Na pasta painel de **projeto** do Unity, **hologramas** , localize o objeto **spacecollection** .
* Arraste e solte o objeto **spacecollection** no painel **hierarquia** .
* No painel **hierarquia** , selecione o objeto **SpatialProcessing** .
* No painel **Inspetor** , localize o componente **Gerenciador de espaço de reprodução (script)** .
* Clique duas vezes em **PlaySpaceManager.cs** para abri-lo no Visual Studio.

PlaySpaceManager.cs contém código específico do aplicativo. Adicionaremos funcionalidade a esse script para habilitar o seguinte comportamento:

1. Parar de coletar dados de mapeamento espacial depois de excedermos o limite de tempo de verificação (10 segundos).
2. Processar os dados de mapeamento espacial:
    1. Use o SurfaceMeshesToPlanes para criar uma representação mais simples do mundo como planos (paredes, andares, tetos, etc.).
    2. Use RemoveSurfaceVertices para remover triângulos de superfície que se enquadram em limites de plano.
3. Gere uma coleção de hologramas no mundo e coloque-os nos planos de parede e piso próximos ao usuário.

Conclua os exercícios de codificação marcados em PlaySpaceManager.cs ou substitua o script pela solução concluída abaixo:

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

**Compilar e implantar**

* Antes de implantar no HoloLens, pressione o botão **reproduzir** no Unity para entrar no modo de reprodução.
* Depois que a malha de sala é carregada do arquivo, aguarde 10 segundos antes de o processamento começar na malha de mapeamento espacial.
* Quando o processamento for concluído, os planos aparecerão para representar o piso, as paredes, o teto etc.
* Depois que todos os planos forem encontrados, você verá que um sistema solar aparecerá em uma tabela de piso perto da câmera.
* Dois cartazes devem aparecer em paredes próximas à câmera também. Alterne para a guia **cena** se você não puder vê-las no modo de **jogo** .
* Pressione o botão **reproduzir** novamente para sair do modo de reprodução.
* Crie e implante no HoloLens, como de costume.
* Aguarde a verificação e o processamento dos dados de mapeamento espacial a serem concluídos.
* Depois de ver os planos, tente encontrar o sistema solar e os pôsteres em seu mundo.

## <a name="chapter-4---placement"></a>Capítulo 4-posicionamento

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Seus**

* Determine se um holograma se ajustará em uma superfície.
* Forneça comentários para o usuário quando um holograma puder/não couber em uma superfície.

**Sobre**

* No painel **hierarquia** do Unity, selecione o objeto **SpatialProcessing** .
* No painel **Inspetor** , encontre as **malhas da superfície para o componente planos (script)** .
* Altere a propriedade **desenhar planos** para **nada** para limpar a seleção.
* Altere a propriedade **desenhar planos** para a **parede**, de modo que somente os planos de parede serão renderizados.
* Na pasta painel do **projeto** , **scripts** , clique duas vezes em **Placeable.cs** para abri-lo no Visual Studio.

O script **posicionável** já está anexado aos cartazes e à caixa de projeção criados após a conclusão da localização do plano. Tudo o que precisamos fazer é remover o comentário de algum código, e esse script irá obter o seguinte:

1. Determine se um holograma caberá em uma superfície por raycasting do centro e quatro cantos do cubo delimitador.
2. Verifique a superfície normal para determinar se ela é tranqüila o suficiente para que o holograma fique liberado.
3. Renderize um cubo delimitador em volta do holograma para mostrar seu tamanho real durante a colocação.
4. Converta uma sombra em/atrás do holograma para mostrar onde ele será colocado no chão/parede.
5. Renderize a sombra como vermelha, se o holograma não puder ser colocado na superfície, ou verde, se puder.
6. Reorientar o holograma para alinhar com o tipo de superfície (vertical ou horizontal) ao qual ele tem afinidade.
7. Posicione suavemente o holograma na superfície selecionada para evitar o comportamento de salto ou de ajuste.

Remova a marca de comentário de todo o código no exercício de codificação abaixo ou use essa solução concluída no **Placeable.cs**:

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
    /// The alignToVerticalSurface parameter is ignored if the object
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

**Compilar e implantar**

* Como antes, compile o projeto e implante-o no HoloLens.
* Aguarde a verificação e o processamento dos dados de mapeamento espacial a serem concluídos.
* Quando você vir o sistema solar, olhar na caixa de projeção abaixo e executar um gesto de seleção para movê-lo. Enquanto a caixa de projeção estiver selecionada, um cubo delimitador ficará visível na caixa de projeção.
* Mova você para o olhar em um local diferente na sala. A caixa de projeção deve seguir seu olhar. Quando a sombra abaixo da caixa de projeção fica vermelha, não é possível posicionar o holograma nessa superfície. Quando a sombra abaixo da caixa de projeção fica verde, você pode posicionar o holograma executando outro gesto de seleção.
* Localize e selecione um dos pôsteres do Holographic em uma parede para movê-lo para um novo local. Observe que você não pode posicionar o pôster no chão ou no teto e que ele permanece corretamente orientado a cada parede à medida que você se movimenta.

## <a name="chapter-5---occlusion"></a>Capítulo 5-oclusão

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Seus**

* Determine se um holograma é obstruído pela malha de mapeamento espacial.
* Aplique diferentes técnicas de oclusão para obter um efeito divertido.

**Sobre**

Primeiro, vamos permitir que a malha de mapeamento espacial occlude outros hologramas sem occluding o mundo real:

* No painel **hierarquia** , selecione o objeto **SpatialProcessing** .
* No painel **Inspetor** , localize o componente **Gerenciador de espaço de reprodução (script)** .
* Clique no círculo à direita da propriedade **material secundário** .
* Localize e selecione o material de **oclusão** e feche a janela.

Em seguida, vamos adicionar um comportamento especial à terra, para que ele tenha um realce azul sempre que ele se tornar obstruído por outro holograma (como o sol) ou pela malha de mapeamento espacial:

* No painel **projeto** , na pasta **hologramas** , expanda o objeto **SolarSystem** .
* Clique em **terra**.
* No painel **Inspetor** , encontre o material da terra (componente inferior).
* Na **lista suspensa sombreador**, altere o sombreador para **personalizado > OcclusionRim**. Isso processará um realce azul em volta da terra sempre que for obstruído por outro objeto.

Por fim, vamos habilitar um efeito de visão x-ray para planetas em nosso sistema solar. Precisaremos editar **PlanetOcclusion.cs** (encontrado na pasta Scripts\SolarSystem) para obter o seguinte:

1. Determine se um planeta é obstruídodo pela camada SpatialMapping (malhas e planos de sala).
2. Mostre a representação delineada de um planeta sempre que ele for obstruído pela camada SpatialMapping.
3. Oculte a representação delineada de um planeta quando ela não estiver bloqueada pela camada SpatialMapping.

Siga o exercício de codificação no PlanetOcclusion.cs ou use a seguinte solução:

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

**Compilar e implantar**

* Crie e implante o aplicativo no HoloLens, como de costume.
* Aguarde a verificação e o processamento dos dados de mapeamento espacial a serem concluídos (você deverá ver as linhas azuis aparecerem nas paredes).
* Localize e selecione a caixa projeção do sistema solar e, em seguida, defina a caixa ao lado de uma parede ou atrás de um contador.
* Você pode exibir os oclusão básicos ocultando as superfícies para o ponto no pôster ou na caixa de projeção.
* Procure a terra, deve haver um efeito de realce azul sempre que ele ficar atrás de outro holograma ou de uma superfície.
* Observe como os planetas se movem para trás da parede ou de outras superfícies na sala. Agora você tem a visão x-ray e pode ver seus esqueletos de wireframe!

## <a name="the-end"></a>Fim

Parabéns! Agora você concluiu o **Sr Spatial 230: mapeamento espacial**.

* Você sabe como verificar seu ambiente e carregar dados de mapeamento espacial para o Unity.
* Você entende os conceitos básicos dos sombreadores e como os materiais podem ser usados para revisualizar o mundo.
* Você aprendeu com novas técnicas de processamento para localizar planos e remover triângulos de uma malha.
* Você conseguiu mover e posicionar hologramas em superfícies que faziam sentido.
* Você experimentou técnicas oclusãos diferentes e aproveitou a potência da visão x-ray!
