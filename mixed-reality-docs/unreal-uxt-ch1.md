---
title: 1. Introdução
description: Parte 1 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: c16671fc8f4233378dafa646786df1f7b5ae18e1
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330163"
---
# <a name="1-getting-started"></a>1. Introdução

Seja você alguém pouco familiarizado com a realidade misturada ou um profissional experiente, esse é o lugar para iniciar seu percurso com o [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) e o [Unreal Engine](https://www.unrealengine.com/en-US/). Esta série de tutoriais fornecerá um guia passo a passo sobre como criar um aplicativo de xadrez interativo com o [plug-in de Ferramentas de UX](https://github.com/microsoft/MixedReality-UXTools-Unreal), parte do [Kit de Ferramentas de Realidade Misturada para o Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal). O plug-in ajudará você a adicionar recursos comuns de UX a seus projetos pelo uso de código, blueprints e exemplos. 

![Encerrar cena no visor](images/unreal-uxt/5-endscene.PNG)

Ao final da série, você terá experiência prática em:
* Criar um projeto
* Configurar a realidade misturada
* Trabalhar com a entrada do usuário
* Adicionar botões
* Jogar em um emulador ou dispositivo

Se você tiver alguma dúvida, confira nossa [Visão geral do desenvolvimento com o Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).

## <a name="prerequisites"></a>Pré-requisitos
Verifique se você atendeu aos seguintes requisitos antes de começar:
* Windows 10 1809 ou posterior
* SDK do Windows 10 10.0.18362.0 ou posterior
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 ou posterior
* Dispositivo do Microsoft HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode) ou Emulador
* Visual Studio 2019 com as cargas de trabalho abaixo

### <a name="installing-visual-studio-2019"></a>Instalação do Visual Studio 2019
A última etapa é configurar o Visual Studio da seguinte maneira:
1. Instale a versão mais recente do [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)
2. Instale as seguintes [cargas de trabalho](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):
    * Desenvolvimento para desktop com C++
    * Desenvolvimento para área de trabalho com .NET
    * Desenvolvimento para a Plataforma Universal do Windows

3. Instale os seguintes [componentes](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):
    * Compiladores, ferramentas de build e runtimes > ferramentas de build MSVC v142 – VS 2019 C++ ARM64 (versão mais recente)

Pronto! Você está pronto para prosseguir para a inicialização do projeto de aplicativo de xadrez.

[Próxima seção: 2. Inicializar o seu projeto e o primeiro aplicativo](unreal-uxt-ch2.md)