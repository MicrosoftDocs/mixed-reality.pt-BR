---
title: Pacotes MRTK
description: Este artigo descreve os pacotes que compõem o Toollkit realidade mista do Microsoft.
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality, MRTK, componente, o pacote
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590928"
---
# <a name="mrtk-packages"></a><span data-ttu-id="bef75-104">Pacotes MRTK</span><span class="sxs-lookup"><span data-stu-id="bef75-104">MRTK packages</span></span>

<span data-ttu-id="bef75-105">O Kit de ferramentas de realidade misturada (MRTK) é uma coleção de pacotes que permitem o desenvolvimento de aplicativos de realidade mista de plataforma cruzada, fornecendo suporte para realidade misturada plataformas de hardware e de maneira modular.</span><span class="sxs-lookup"><span data-stu-id="bef75-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms in a componentized manner.</span></span>

<span data-ttu-id="bef75-106">Há três categorias de pacotes MRTK:</span><span class="sxs-lookup"><span data-stu-id="bef75-106">There are three categories of MRTK packages:</span></span> 

* [<span data-ttu-id="bef75-107">Foundation</span><span class="sxs-lookup"><span data-stu-id="bef75-107">Foundation</span></span>](#foundation-packages)
* [<span data-ttu-id="bef75-108">Extensão</span><span class="sxs-lookup"><span data-stu-id="bef75-108">Extension</span></span>](#extension-packages)
* [<span data-ttu-id="bef75-109">Experimental</span><span class="sxs-lookup"><span data-stu-id="bef75-109">Experimental</span></span>](#experimental-packages)

## <a name="foundation-packages"></a><span data-ttu-id="bef75-110">Pacotes de base</span><span class="sxs-lookup"><span data-stu-id="bef75-110">Foundation Packages</span></span>

<span data-ttu-id="bef75-111">A base de kit de ferramentas de realidade mista é o conjunto de pacotes que permitem que seu aplicativo aproveitar a funcionalidade comum entre as plataformas de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="bef75-111">The Mixed Reality Toolkit Foundation is the set of packages that enable your application to leverage common functionality across Mixed Reality Platforms.</span></span> <span data-ttu-id="bef75-112">Esses pacotes são liberados e suporte da Microsoft do código-fonte na [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) ramificação no GitHub.</span><span class="sxs-lookup"><span data-stu-id="bef75-112">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

![MRTK Foundation pacotes](images/mrtk-foundation.jpg)

<span data-ttu-id="bef75-114">*Pacotes de base do Kit de ferramentas de realidade mistos*</span><span class="sxs-lookup"><span data-stu-id="bef75-114">*Mixed Reality Toolkit Foundation packages*</span></span>

<span data-ttu-id="bef75-115">A base de MRTK é composta de:</span><span class="sxs-lookup"><span data-stu-id="bef75-115">The MRTK Foundation is comprised of:</span></span>

* [<span data-ttu-id="bef75-116">Pacote de núcleo</span><span class="sxs-lookup"><span data-stu-id="bef75-116">Core Package</span></span>](#core-package)
* [<span data-ttu-id="bef75-117">Provedores de plataforma</span><span class="sxs-lookup"><span data-stu-id="bef75-117">Platform Providers</span></span>](#platform-providers)
* [<span data-ttu-id="bef75-118">Serviços do sistema</span><span class="sxs-lookup"><span data-stu-id="bef75-118">System Services</span></span>](#system-services)
* [<span data-ttu-id="bef75-119">Ativos de recurso</span><span class="sxs-lookup"><span data-stu-id="bef75-119">Feature Assets</span></span>](#feature-assets)

<span data-ttu-id="bef75-120">As seções a seguir descrevem os tipos de pacotes em cada categoria.</span><span class="sxs-lookup"><span data-stu-id="bef75-120">The following sections describe the types of packages in each category.</span></span>

### <a name="core-package"></a><span data-ttu-id="bef75-121">Pacote de núcleo</span><span class="sxs-lookup"><span data-stu-id="bef75-121">Core Package</span></span>

<span data-ttu-id="bef75-122">O pacote principal é um _necessária_ componente e é executada como uma dependência por todos os pacotes de foundation MRTK.</span><span class="sxs-lookup"><span data-stu-id="bef75-122">The core package is a _required_ component and is taken as a dependency by all MRTK foundation packages.</span></span>

<span data-ttu-id="bef75-123">O pacote MRTK Core inclui:</span><span class="sxs-lookup"><span data-stu-id="bef75-123">The MRTK Core package includes:</span></span>

* [<span data-ttu-id="bef75-124">Tipos de dados, interfaces e classes comuns</span><span class="sxs-lookup"><span data-stu-id="bef75-124">Common interfaces, classes and data types</span></span>](#common-interfaces-clases-and-data-types)
* [<span data-ttu-id="bef75-125">Componente de cena MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="bef75-125">MixedRealityToolkit scene component</span></span>](#mixedrealitytoolkit-scene-component)
* [<span data-ttu-id="bef75-126">Sombreador MRTK padrão</span><span class="sxs-lookup"><span data-stu-id="bef75-126">MRTK Standard Shader</span></span>](#mrtk-standard-shader)
* [<span data-ttu-id="bef75-127">Provedor de entrada do Unity</span><span class="sxs-lookup"><span data-stu-id="bef75-127">Unity Input Provider</span></span>](#unity-input-provider)
* [<span data-ttu-id="bef75-128">Gerenciamento de pacotes</span><span class="sxs-lookup"><span data-stu-id="bef75-128">Package Management</span></span>](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a><span data-ttu-id="bef75-129">Tipos de dados, interfaces e classes comuns</span><span class="sxs-lookup"><span data-stu-id="bef75-129">Common interfaces, classes and data types</span></span>

<span data-ttu-id="bef75-130">O pacote de núcleo de kit de ferramentas de realidade mista contém as definições para todas as interfaces comuns, classes e tipos de dados que são usados por todos os outros componentes.</span><span class="sxs-lookup"><span data-stu-id="bef75-130">The Mixed Reality Toolkit Core package contains the definitions for all of the common interfaces, classes and data types that are used by all other components.</span></span> <span data-ttu-id="bef75-131">É altamente recomendável que os aplicativos acessar componentes MRTK exclusivamente por meio de interfaces definidas para permitir o maior nível de compatibilidade entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="bef75-131">It is highly recommended that applications access MRTK components exclusively through the defined interfaces to enable the highest level of compatibility across platforms.</span></span>

#### <a name="mixedrealitytoolkit-scene-component"></a><span data-ttu-id="bef75-132">Componente de cena MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="bef75-132">MixedRealityToolkit scene component</span></span>

<span data-ttu-id="bef75-133">O componente de cena MixedRealityToolkit é o Gerenciador de recursos único e centralizado para o Kit de ferramentas de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="bef75-133">The MixedRealityToolkit scene component is the single, centralized resource manager for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="bef75-134">Esse componente carrega e gerencia o tempo de vida dos módulos do serviço e plataforma e fornece recursos para os sistemas acessar suas definições de configuração.</span><span class="sxs-lookup"><span data-stu-id="bef75-134">This component loads and manages the lifespan of the platform and service modules and provides resources for the systems to access their configuration settings.</span></span> 

#### <a name="mrtk-standard-shader"></a><span data-ttu-id="bef75-135">Sombreador MRTK padrão</span><span class="sxs-lookup"><span data-stu-id="bef75-135">MRTK Standard Shader</span></span>

<span data-ttu-id="bef75-136">O sombreador padrão do MRTK fornece a base para praticamente todos os materiais fornecidos pelo MRTK.</span><span class="sxs-lookup"><span data-stu-id="bef75-136">The MRTK Standard Shader provides the basis for virtually all of the materials provided by the MRTK.</span></span> <span data-ttu-id="bef75-137">Esse sombreador é extremamente flexível e otimizado para a variedade de plataformas em que há suporte para MRTK.</span><span class="sxs-lookup"><span data-stu-id="bef75-137">This shader is extremely flexible and optimized for the variety of platforms on which MRTK is supported.</span></span> <span data-ttu-id="bef75-138">Vale _altamente_ recomendado que o material do seu aplicativo usa o sombreador padrão de MRTK para otimizar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="bef75-138">It is _highly_ recommended that your application's materials use the MRTK standard shader for optimal performance.</span></span>

#### <a name="unity-input-provider"></a><span data-ttu-id="bef75-139">Provedor de entrada do Unity</span><span class="sxs-lookup"><span data-stu-id="bef75-139">Unity Input Provider</span></span>

<span data-ttu-id="bef75-140">O provedor de entrada do Unity fornece acesso a dispositivos de entrada comuns, como controladores de jogos, telas sensíveis ao toque e mouse espacial 3D.</span><span class="sxs-lookup"><span data-stu-id="bef75-140">The Unity Input Provider provides access to common input devices such as game controllers, touch screens and a 3D spatial mouse.</span></span>

#### <a name="package-management"></a><span data-ttu-id="bef75-141">Gerenciamento de pacotes</span><span class="sxs-lookup"><span data-stu-id="bef75-141">Package Management</span></span>

<span data-ttu-id="bef75-142">_Em breve_</span><span class="sxs-lookup"><span data-stu-id="bef75-142">_Coming soon_</span></span>

<span data-ttu-id="bef75-143">O pacote de núcleo de kit de ferramentas de realidade mista oferece suporte para descobrir e gerenciar foundation opcional, extensão e pacotes MRTK experimentais.</span><span class="sxs-lookup"><span data-stu-id="bef75-143">The Mixed Reality Toolkit Core package provides support for discovering and managing the optional foundation, extension and experimental MRTK packages.</span></span>

### <a name="platform-providers"></a><span data-ttu-id="bef75-144">Provedores de plataforma</span><span class="sxs-lookup"><span data-stu-id="bef75-144">Platform Providers</span></span>

<span data-ttu-id="bef75-145">Os pacotes de provedor de plataforma MRTK são os componentes que habilitam o Kit de ferramentas de realidade mista para hardware de realidade mista de destino e a funcionalidade de plataforma.</span><span class="sxs-lookup"><span data-stu-id="bef75-145">The MRTK Platform Provider packages are the components that enable the Mixed Reality Toolkit to target Mixed Reality hardware and platform functionality.</span></span>

<span data-ttu-id="bef75-146">Plataformas com suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="bef75-146">Supported platforms include:</span></span>

* [<span data-ttu-id="bef75-147">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bef75-147">Windows Mixed Reality</span></span>](#windows-mixed-reality)
* [<span data-ttu-id="bef75-148">OpenVR</span><span class="sxs-lookup"><span data-stu-id="bef75-148">OpenVR</span></span>](#openvr)
* [<span data-ttu-id="bef75-149">Windows Voice</span><span class="sxs-lookup"><span data-stu-id="bef75-149">Windows Voice</span></span>](#windows-voice)

#### <a name="windows-mixed-reality"></a><span data-ttu-id="bef75-150">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bef75-150">Windows Mixed Reality</span></span>

<span data-ttu-id="bef75-151">O pacote do Windows Mixed Reality oferece suporte para dispositivos Microsoft HoloLens e Windows misto realidade envolventes.</span><span class="sxs-lookup"><span data-stu-id="bef75-151">The Windows Mixed Reality package provides support for Microsoft HoloLens and Windows Mixed Reality Immersive devices.</span></span> <span data-ttu-id="bef75-152">O pacote contém suporte de plataforma completo, incluindo:</span><span class="sxs-lookup"><span data-stu-id="bef75-152">The package contains full platform support, including:</span></span>

* <span data-ttu-id="bef75-153">Mantenha o foco de direcionamento</span><span class="sxs-lookup"><span data-stu-id="bef75-153">Gaze targeting</span></span>
* <span data-ttu-id="bef75-154">Gestos</span><span class="sxs-lookup"><span data-stu-id="bef75-154">Gestures</span></span>
* <span data-ttu-id="bef75-155">Controladores de movimento de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="bef75-155">Windows Mixed Reality Motion controllers</span></span>
* <span data-ttu-id="bef75-156">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="bef75-156">Spatial Mapping</span></span>

#### <a name="openvr"></a><span data-ttu-id="bef75-157">OpenVR</span><span class="sxs-lookup"><span data-stu-id="bef75-157">OpenVR</span></span>

<span data-ttu-id="bef75-158">O pacote de OpenVR fornece a plataforma de hardware e suportam para dispositivos que usam a plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="bef75-158">The OpenVR package provides hardware and platform support for devices using the OpenVR platform.</span></span>

#### <a name="windows-voice"></a><span data-ttu-id="bef75-159">Voz do Windows</span><span class="sxs-lookup"><span data-stu-id="bef75-159">Windows Voice</span></span>

<span data-ttu-id="bef75-160">O pacote de voz do Windows oferece suporte para a funcionalidade de reconhecimento e ditado de palavra-chave em dispositivos Microsoft Windows 10.</span><span class="sxs-lookup"><span data-stu-id="bef75-160">The Windows Voice package provides support for keyword recognition and dictation functionality on Microsoft Windows 10 devices.</span></span>

### <a name="system-services"></a><span data-ttu-id="bef75-161">Serviços do sistema</span><span class="sxs-lookup"><span data-stu-id="bef75-161">System Services</span></span>

<span data-ttu-id="bef75-162">Principais serviços de plataforma são fornecidos em pacotes de serviço do sistema.</span><span class="sxs-lookup"><span data-stu-id="bef75-162">Core platform services are provided in system service packages.</span></span> <span data-ttu-id="bef75-163">Esses pacotes contêm implementações de padrão do Toolkit de realidade misturada das interfaces de serviço de sistema, definidas na [core](#core-package) pacote.</span><span class="sxs-lookup"><span data-stu-id="bef75-163">These packages contain the Mixed Reality Toolkit's default implementations of the system service interfaces, defined in the [core](#core-package) package.</span></span>

<span data-ttu-id="bef75-164">A base MRTK inclui os seguintes serviços do sistema:</span><span class="sxs-lookup"><span data-stu-id="bef75-164">The MRTK foundation includes the following system services:</span></span>

* [<span data-ttu-id="bef75-165">Sistema de limite</span><span class="sxs-lookup"><span data-stu-id="bef75-165">Boundary System</span></span>](#boundary-system)
* [<span data-ttu-id="bef75-166">Sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="bef75-166">Diagnostic System</span></span>](#diagnostic-system)
* [<span data-ttu-id="bef75-167">Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="bef75-167">Input System</span></span>](#input-system)
* [<span data-ttu-id="bef75-168">Sistema de percepção espacial</span><span class="sxs-lookup"><span data-stu-id="bef75-168">Spatial Awareness System</span></span>](#spatial-awareness-system)
* [<span data-ttu-id="bef75-169">Sistema de ser transportado</span><span class="sxs-lookup"><span data-stu-id="bef75-169">Teleport System</span></span>](#teleport-system)

#### <a name="boundary-system"></a><span data-ttu-id="bef75-170">Sistema de limite</span><span class="sxs-lookup"><span data-stu-id="bef75-170">Boundary System</span></span>

<span data-ttu-id="bef75-171">O sistema de limite MRTK fornece dados sobre a realidade para virtual playspace.</span><span class="sxs-lookup"><span data-stu-id="bef75-171">The MRTK Boundary System provides data about the to virtual reality playspace.</span></span> <span data-ttu-id="bef75-172">Em sistemas para os quais o usuário tiver configurado o limite, o sistema pode fornecer um plano de chão, playspace retangular, área controlada e muito mais.</span><span class="sxs-lookup"><span data-stu-id="bef75-172">On systems for which the user has configured the boundary, the system can provide a floor plane, rectangular playspace, tracked area, and more.</span></span>

#### <a name="diagnostic-system"></a><span data-ttu-id="bef75-173">Sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="bef75-173">Diagnostic System</span></span>

<span data-ttu-id="bef75-174">O sistema de diagnóstico MRTK fornece dados de desempenho em tempo real dentro de sua experiência de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bef75-174">The MRTK Diagnostic System provides real-time performance data within your application experience.</span></span> <span data-ttu-id="bef75-175">Em um as, você poderá exibir a taxa de quadros, tempo de processador e outras principais métricas de desempenho que você use seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bef75-175">At a glace, you will be able to view frame rate, processor time and other key performance metrics as you use your application.</span></span>

#### <a name="input-system"></a><span data-ttu-id="bef75-176">Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="bef75-176">Input System</span></span>

<span data-ttu-id="bef75-177">Os sistemas de entrada MRTK permite que os aplicativos acessar a entrada de uma maneira de plataforma cruzada especificando ações do usuário e atribuir essas ações para os botões mais apropriados e os eixos em controladores de destino.</span><span class="sxs-lookup"><span data-stu-id="bef75-177">The MRTK Input Systems enables applications to access input in a cross platform manner by specifying user actions and assigning those actions to the most appropriate buttons and axes on target controllers.</span></span>

#### <a name="spatial-awareness-system"></a><span data-ttu-id="bef75-178">Sistema de percepção espacial</span><span class="sxs-lookup"><span data-stu-id="bef75-178">Spatial Awareness System</span></span>

<span data-ttu-id="bef75-179">O sistema de percepção espacial MRTK permite acesso a dados ambientais do mundo real de dispositivos, como o Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bef75-179">The MRTK Spatial Awareness System enables access to real-world environmental data from devices such as the Microsoft HoloLens.</span></span>

#### <a name="teleport-system"></a><span data-ttu-id="bef75-180">Sistema de ser transportado</span><span class="sxs-lookup"><span data-stu-id="bef75-180">Teleport System</span></span>

<span data-ttu-id="bef75-181">O sistema de ser transportado MRTK fornece suporte de locomotion de realidade virtual.</span><span class="sxs-lookup"><span data-stu-id="bef75-181">The MRTK Teleport System provides virtual reality locomotion support.</span></span>

### <a name="feature-assets"></a><span data-ttu-id="bef75-182">Ativos de recurso</span><span class="sxs-lookup"><span data-stu-id="bef75-182">Feature Assets</span></span>

<span data-ttu-id="bef75-183">Ativos de recurso são coleções de funcionalidades relacionadas fornecidos, como scripts e ativos do Unity.</span><span class="sxs-lookup"><span data-stu-id="bef75-183">Feature Assets are collections of related functionality delivered as Unity assets and scripts.</span></span> <span data-ttu-id="bef75-184">Alguns desses recursos incluem:</span><span class="sxs-lookup"><span data-stu-id="bef75-184">Some of these features include:</span></span>

* <span data-ttu-id="bef75-185">Controles de Interface do usuário</span><span class="sxs-lookup"><span data-stu-id="bef75-185">User Interface Controls</span></span>
* <span data-ttu-id="bef75-186">Recursos padrão</span><span class="sxs-lookup"><span data-stu-id="bef75-186">Standard Assets</span></span>
* <span data-ttu-id="bef75-187">more</span><span class="sxs-lookup"><span data-stu-id="bef75-187">more</span></span>

## <a name="extension-packages"></a><span data-ttu-id="bef75-188">Pacotes de extensão</span><span class="sxs-lookup"><span data-stu-id="bef75-188">Extension Packages</span></span>

<span data-ttu-id="bef75-189">Pacotes de extensão MRTK são uma coleção de pacotes escritos pela Microsoft e pela comunidade que estendem e melhoram a funcionalidade do Kit de ferramentas de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="bef75-189">MRTK Extension packages are a collection of packages written by Microsoft and the Community that extend and enhance the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="bef75-190">Os autores de extensão serão as dependências necessárias de estado, marcar o pacote como compatível com o Kit de ferramentas de realidade mista e fornecer licenciamento e dão suporte a instruções.</span><span class="sxs-lookup"><span data-stu-id="bef75-190">Extension authors will state any required dependencies, mark the package as compatible with the Mixed Reality Toolkit and provide licensing and support statements.</span></span>

<span data-ttu-id="bef75-191">Pacotes de extensão podem fornecer novos recursos e suporte a nova plataforma.</span><span class="sxs-lookup"><span data-stu-id="bef75-191">Extension packages may provide new features and new platform support.</span></span> <span data-ttu-id="bef75-192">Ao longo do tempo, as extensões podem, com a assistência e aprovação dos autores, ser migradas para a base de MRTK no tempo em que eles serão lançados e suporte da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bef75-192">Over time, extensions may, with the assistance and approval of the authors, be migrated into the MRTK Foundation at which time they will be released and supported by Microsoft.</span></span>

![Pacote de extensão MRTK](images/mrtk-extensions.jpg)

<span data-ttu-id="bef75-194">*Pacotes de extensão do Kit de ferramentas de realidade mistos*</span><span class="sxs-lookup"><span data-stu-id="bef75-194">*Mixed Reality Toolkit Extension packages*</span></span>

## <a name="experimental-packages"></a><span data-ttu-id="bef75-195">Pacotes experimentais</span><span class="sxs-lookup"><span data-stu-id="bef75-195">Experimental Packages</span></span>

<span data-ttu-id="bef75-196">Pacotes experimentais fornecem a capacidade de recursos de protótipo de voo, versões de pré-lançamento e novas ideias interessantes.</span><span class="sxs-lookup"><span data-stu-id="bef75-196">Experimental packages provide the ability to flight prototype features, pre-releases and exciting new ideas.</span></span> <span data-ttu-id="bef75-197">O objetivo de pacotes mais experimentais é tentar algo novo e avaliar o interesse do cliente.</span><span class="sxs-lookup"><span data-stu-id="bef75-197">The goal of most experimental packages is to try something new and to gauge customer interest.</span></span> <span data-ttu-id="bef75-198">Muitos, embora nem todos pacotes experimentais será lançados novamente como extensões quando a criação de protótipos e a fase de teste for concluído.</span><span class="sxs-lookup"><span data-stu-id="bef75-198">Many, though not all, experimental packages will be re-released as extensions once the prototyping and testing phase completes.</span></span>

![Pacotes MRTK Experimental](images/mrtk-experimental.jpg)

<span data-ttu-id="bef75-200">*Pacotes Experimental de kit de ferramentas de realidade mistos*</span><span class="sxs-lookup"><span data-stu-id="bef75-200">*Mixed Reality Toolkit Experimental packages*</span></span>

## <a name="conclusion"></a><span data-ttu-id="bef75-201">Conclusão</span><span class="sxs-lookup"><span data-stu-id="bef75-201">Conclusion</span></span>

<span data-ttu-id="bef75-202">Os pacotes de kit de ferramentas de realidade mista e o sistema de gerenciamento de pacotes são projetados para habilitar um método simple e transparente para você criar fogo recursos às suas experiências sem a necessidade de componentes desnecessários a serem incluídos no projeto.</span><span class="sxs-lookup"><span data-stu-id="bef75-202">The Mixed Reality Toolkit packages and package management system are designed to enable a clean and simple method for you to additively build features into your experiences without requiring unnecessary components to be included into the project.</span></span>

<span data-ttu-id="bef75-203">Ao longo do tempo, o suporte ao gerenciamento de pacote será adicionado e aprimorado no Toolkit de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="bef75-203">Over time, package management support will be added and enhanced within the Mixed Reality Toolkit.</span></span> <span data-ttu-id="bef75-204">Se você tiver comentários ou deseja se envolver, visite o [Kit de ferramentas de realidade misturada projeto](https://github.com/Microsoft/MixedRealityToolkit-Unity) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="bef75-204">If you have feedback or wish to get involved, please visit the [Mixed Reality Toolkit project](https://github.com/Microsoft/MixedRealityToolkit-Unity) on GitHub.</span></span> 

## <a name="see-also"></a><span data-ttu-id="bef75-205">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bef75-205">See also</span></span>

* [<span data-ttu-id="bef75-206">MixedRealityToolkit-Unity (GitHub)</span><span class="sxs-lookup"><span data-stu-id="bef75-206">MixedRealityToolkit-Unity (GitHub)</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

