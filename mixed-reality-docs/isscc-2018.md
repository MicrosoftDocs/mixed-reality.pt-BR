---
title: White paper da câmera de profundidade - ISSCC 2018
description: White paper técnico discutindo a câmera de profundidade a serem utilizadas no projeto Kinect para o Azure e a próxima versão do HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: eventos, iscc, pesquisa Visual computacional, pesquisas, kinect, hololens, profundidade, ' TOF '
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589789"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="cd233-104">White paper da câmera de profundidade - ISSCC 2018</span><span class="sxs-lookup"><span data-stu-id="cd233-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="cd233-105">**Título:** 1Mpixel 65nm BSI 320MHz demodulado ' TOF ' imagem Sensor com 3.5μm Pixels do obturador Global e a compartimentalização analógico</span><span class="sxs-lookup"><span data-stu-id="cd233-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="cd233-106">**Colaboradores:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Elkhatib Tamer, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, painel neve, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Henrique Vei Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span><span class="sxs-lookup"><span data-stu-id="cd233-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="cd233-107">**Apresentado no ISSCC 2018 e publicados no ISSCC graus. Tech. Documentos, fevereiro de 2018.**</span><span class="sxs-lookup"><span data-stu-id="cd233-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="cd233-108">C.</span><span class="sxs-lookup"><span data-stu-id="cd233-108">C.</span></span> <span data-ttu-id="cd233-109">Bamji et al., "1Mpixel 65nm BSI 320MHz demodulado ' TOF ' imagem Sensor com 3.5μm Pixels do obturador Global e compartimentalização analógica," ISSCC graus.</span><span class="sxs-lookup"><span data-stu-id="cd233-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="cd233-110">Tech.</span><span class="sxs-lookup"><span data-stu-id="cd233-110">Tech.</span></span> <span data-ttu-id="cd233-111">Documentos, PP 94-95, fevereiro de 2018.</span><span class="sxs-lookup"><span data-stu-id="cd233-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="cd233-112">Explore o IEEE Link: https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="cd233-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="cd233-113">© 2018 IEEE.</span><span class="sxs-lookup"><span data-stu-id="cd233-113">© 2018 IEEE.</span></span> <span data-ttu-id="cd233-114">É permitido o uso pessoal deste material.</span><span class="sxs-lookup"><span data-stu-id="cd233-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="cd233-115">Permissão do IEEE deve ser obtida para todos os outros usos, em qualquer mídia atuais ou futuros, incluindo reimpressão/republicação deste material para fins de propaganda ou promocionais, Criando nova funciona coletiva, para revenda ou redistribuição para servidores ou listas, ou reutilização de qualquer componente protegido por direitos autorais desse trabalho em outros trabalhos.</span><span class="sxs-lookup"><span data-stu-id="cd233-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="cd233-116">**White paper:**</span><span class="sxs-lookup"><span data-stu-id="cd233-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="cd233-117">![Visualização do white paper](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="cd233-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="cd233-118">Baixe o whitepaper de câmera de profundidade</span><span class="sxs-lookup"><span data-stu-id="cd233-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
