# <a name="unity"></a>[Unity](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1. Baixar a última versão

Recomendamos usar o fluxo [LTS (Suporte de Longo Prazo) do Unity](https://unity3d.com/unity/qa/lts-releases), pois ele é a melhor versão para iniciar projetos. Atualize para a última revisão para obter as correções estáveis mais recentes. 
* A recomendação atual é usar o **Unity 2019**, que é o build LTS necessário para o MRTK v2 abaixo.
* Caso você precise usar outra versão do Unity por motivos específicos, o Unity dá suporte a instalações lado a lado de versões diferentes.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importar o MRTK (Kit de Ferramentas de Realidade Misturada)
![MRTK](../images/UX/MRTK_UX_Hero.png)

O [MRTK](../mrtk-getting-started.md) (Kit de Ferramentas de Realidade Misturada) é um kit de desenvolvimento multiplataforma de software livre para aplicativos de realidade misturada. O MRTK fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. O kit de ferramentas destina-se a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)<br>**Kit de Ferramentas de Realidade Misturada – Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Se você não quiser usar o MRTK para o Unity, precisará criar o script de todas as interações e todos os comportamentos por conta própria.

#### <a name="other-tools-optional"></a>Outras ferramentas [opcional]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Kit Complementar de Realidade Misturada (GitHub)</a> – bits de código e componentes que não podem ser executados diretamente no HoloLens ou nos headsets imersivos (VR), mas que se emparelham com eles para criar experiências destinadas ao Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Kit de Ferramentas de Realidade Misturada – Comum (GitHub)</a> – uma coleção de scripts e componentes compartilhados.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurar seu computador para o desenvolvimento de Realidade Misturada

O SDK do Windows 10 funciona melhor no sistema operacional Windows 10. Esse SDK também é compatível com: Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Observe que nem todas as ferramentas são compatíveis com sistemas operacionais mais antigos. 

> [!NOTE]
> Desenvolva e implante seus aplicativos para o HoloLens, os headsets imersivos de VR ou ambos. Verifique se você atende aos requisitos abaixo, dependendo das suas necessidades.

#### <a name="for-hololens-development"></a>Desenvolvimento para o HoloLens

Ao configurar seu computador para o desenvolvimento para o HoloLens, verifique se ele atende aos requisitos de sistema do <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> e o <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Se você pretende usar o [emulador do HoloLens](../using-the-hololens-emulator.md), verifique se o computador também atende aos [requisitos do sistema do emulador do HoloLens](../using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Para começar a usar o emulador do HoloLens, veja [Usando o emulador do HoloLens](../using-the-hololens-emulator.md).

Se você planeja desenvolver para headsets imersivos (VR) do HoloLens e do Windows Mixed Reality, use as recomendações e requisitos de sistema descritos na próxima seção.

#### <a name="immersive-vr-headset-requirements"></a>Requisitos do headset imersivo (VR)

>[!NOTE]
>As orientações a seguir são as especificações atuais mínimas e recomendadas para seu *computador de desenvolvimento* para headset imersivo (VR) e são atualizadas regularmente.

>[!WARNING]
>Não confunda essas informações com as [diretrizes de compatibilidade mínima de hardware do computador](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que descreve as *especificações do computador do consumidor*, que é o alvo do seu jogo ou aplicativo de headset imersivo (VR).

Se seu computador de desenvolvimento de headset imersivo não tiver portas HDMI e/ou USB 3.0 padrão, você precisará de [adaptadores](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para conectar o headset.

Atualmente, há [problemas conhecidos](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) com algumas configurações de hardware, especialmente em notebooks com gráficos híbridos.

<table>
<tr>
<th></th><th> Mínimo</th><th> Recomendado</th>
</tr><tr>
<td> Processador</td><td> <b>Notebook:</b> CPU Intel Mobile Core i5 de 7ª geração, Dual-Core com Hyper Threading <b>Área de trabalho:</b> CPU Intel i5 de 6ª geração, Dual-Core com Hyper Threading <b>OU</b> equivalente a AMD FX4350 4,2Ghz Quad-Core</td><td> <b>Área de trabalho</b>: Intel i7 de 6ª geração (6 núcleos) <b>OU</b> GPU AMD Ryzen 5 1600 (6 núcleos, 12 threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> NVIDIA GTX 965M, GPU equivalente ou superior a AMD RX 460M (2GB) com capacidade DX12 <b>Computador:</b> NVIDIA GTX 960/1050, GPU equivalente ou superior a AMD Radeon RX 460 (2GB) com capacidade DX12</td><td><b>Área de trabalho</b>: NVIDIA GTX 980/1060, GPU equivalente ou superior a AMD Radeon RX 480 (2GB) com capacidade DX12</td>
</tr><tr>
<td> Versão WDDM do driver da GPU</td><td colspan="2"> Driver WDDM 2.2</td>
</tr><tr>
<td> Potência do design térmico</td><td colspan="2"> 15W ou mais</td>
</tr><tr>
<td> Portas de vídeo</td><td colspan="2"> 1 x porta de vídeo disponível para headset (HDMI 1.4 ou DisplayPort 1.2 para headsets de 60Hz, HDMI 2.0 ou DisplayPort 1.2 para headsets de 90Hz)</td>
</tr><tr>
<td> Resolução da tela</td><td colspan="2"> Resolução: SVGA (800 x 600) ou maior Profundidade de bits: 32 bits de cores por pixel</td>
</tr><tr>
<td> Memória</td><td> 8 GB de RAM ou mais</td><td> 16 GB de RAM ou mais</td>
</tr><tr>
<td> Armazenamento</td><td colspan="2"> &gt;10 GB de espaço livre adicional</td>
</tr><tr>
<td> Portas USB</td><td colspan="2"> 1 x porta USB disponível para headset (USB 3.0 Tipo A) <b>Observação: a USB deve fornecer um mínimo de 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (para conexão de acessórios)</td>
</tr>
</table>

### <a name="whats-next"></a>E agora?

> [!div class="nextstepaction"]
> [Comece sua jornada no Unity](../unity-development-overview.md)

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1. Baixar a última versão

Recomendamos instalar o [Unreal Engine versão 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) ou posterior para aproveitar ao máximo o suporte interno ao HoloLens.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importar o MRTK (Kit de Ferramentas de Realidade Misturada)
![MRTK](../images/UX/MRTK_UX_Hero.png)

O MRTK (Kit de Ferramentas de Realidade Misturada) é um kit de desenvolvimento multiplataforma de software livre para aplicativos de realidade misturada. O MRTK fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. O kit de ferramentas destina-se a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)<br>**Kit de Ferramentas de Realidade Misturada – Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Se você não quiser usar o MRTK para o Unreal, precisará criar o script de todas as interações e todos os comportamentos por conta própria.

#### <a name="other-tools-optional"></a>Outras ferramentas [opcional]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Kit Complementar de Realidade Misturada (GitHub)</a> – bits de código e componentes que não podem ser executados diretamente no HoloLens ou nos headsets imersivos (VR), mas que se emparelham com eles para criar experiências destinadas ao Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Kit de Ferramentas de Realidade Misturada – Comum (GitHub)</a>: uma coleção de scripts e componentes compartilhados.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurar seu computador para o desenvolvimento de realidade misturada

O SDK do Windows 10 funciona melhor no sistema operacional Windows 10. Esse SDK também é compatível com: Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Observe que nem todas as ferramentas são compatíveis com sistemas operacionais mais antigos. 

> [!NOTE]
> Desenvolva e implante seus aplicativos para o HoloLens, os headsets imersivos de VR ou ambos. Verifique se você atende aos requisitos abaixo, dependendo das suas necessidades.

#### <a name="for-hololens-development"></a>Desenvolvimento para o HoloLens

Ao configurar seu computador para o desenvolvimento no HoloLens, verifique se você atende aos requisitos do sistema do [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) e do <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Se você pretende usar o [emulador do HoloLens](../using-the-hololens-emulator.md), verifique se o computador também atende aos [requisitos do sistema do emulador do HoloLens](../using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Se você planeja desenvolver para headsets imersivos (VR) do HoloLens e do Windows Mixed Reality, use as recomendações e requisitos de sistema descritos na próxima seção.

#### <a name="immersive-vr-headset-requirements"></a>Requisitos do headset imersivo (VR)

>[!NOTE]
>As orientações a seguir são as especificações atuais mínimas e recomendadas para seu *computador de desenvolvimento* para headset imersivo (VR) e são atualizadas regularmente.

>[!WARNING]
>Não confunda essas informações com as [diretrizes de compatibilidade mínima de hardware do computador](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que descreve as *especificações do computador do consumidor*, que é o alvo do seu jogo ou aplicativo de headset imersivo (VR).

Se seu computador de desenvolvimento de headset imersivo não tiver portas HDMI e/ou USB 3.0 padrão, você precisará de [adaptadores](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para conectar o headset.

Atualmente, há [problemas conhecidos](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) com algumas configurações de hardware, especialmente em notebooks com gráficos híbridos.

<table>
<tr>
<th></th><th> Mínimo</th><th> Recomendado</th>
</tr><tr>
<td> Processador</td><td> <b>Notebook:</b> CPU Intel Mobile Core i5 de 7ª geração, Dual-Core com Hyper Threading <b>Área de trabalho:</b> CPU Intel i5 de 6ª geração, Dual-Core com Hyper Threading <b>OU</b> equivalente a AMD FX4350 4,2Ghz Quad-Core</td><td> <b>Área de trabalho</b>: Intel i7 de 6ª geração (6 núcleos) <b>OU</b> GPU AMD Ryzen 5 1600 (6 núcleos, 12 threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> NVIDIA GTX 965M, GPU equivalente ou superior a AMD RX 460M (2GB) com capacidade DX12 <b>Computador:</b> NVIDIA GTX 960/1050, GPU equivalente ou superior a AMD Radeon RX 460 (2GB) com capacidade DX12</td><td><b>Área de trabalho</b>: NVIDIA GTX 980/1060, GPU equivalente ou superior a AMD Radeon RX 480 (2GB) com capacidade DX12</td>
</tr><tr>
<td> Versão WDDM do driver da GPU</td><td colspan="2"> Driver WDDM 2.2</td>
</tr><tr>
<td> Potência do design térmico</td><td colspan="2"> 15W ou mais</td>
</tr><tr>
<td> Portas de vídeo</td><td colspan="2"> 1 x porta de vídeo disponível para headset (HDMI 1.4 ou DisplayPort 1.2 para headsets de 60Hz, HDMI 2.0 ou DisplayPort 1.2 para headsets de 90Hz)</td>
</tr><tr>
<td> Resolução da tela</td><td colspan="2"> Resolução: SVGA (800 x 600) ou maior Profundidade de bits: 32 bits de cores por pixel</td>
</tr><tr>
<td> Memória</td><td> 8 GB de RAM ou mais</td><td> 16 GB de RAM ou mais</td>
</tr><tr>
<td> Armazenamento</td><td colspan="2"> &gt;10 GB de espaço livre adicional</td>
</tr><tr>
<td> Portas USB</td><td colspan="2"> 1 x porta USB disponível para headset (USB 3.0 Tipo A) <b>Observação: a USB deve fornecer um mínimo de 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (para conexão de acessórios)</td>
</tr>
</table>

### <a name="whats-next"></a>E agora?

> [!div class="nextstepaction"]
> [Comece sua jornada no Unreal](../unreal-development-overview.md)

# <a name="native-openxr"></a>[Nativo (OpenXR)](#tab/native)

 ![Desenvolvimento nativo de aplicativos](../images/native_logo_banner.png)

O desenvolvimento de OpenXR nativo não tem um mecanismo para download. Encontre tudo de que precisa para iniciar o desenvolvimento no documento [Introdução ao OpenXR](../openxr-getting-started.md).

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1. Configurar seu computador para o desenvolvimento de realidade misturada

O SDK do Windows 10 funciona melhor no sistema operacional Windows 10. Esse SDK também é compatível com: Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Observe que nem todas as ferramentas são compatíveis com sistemas operacionais mais antigos.

#### <a name="for-hololens-development"></a>Desenvolvimento para o HoloLens

Ao configurar seu computador para o desenvolvimento no HoloLens, verifique se você atende aos requisitos do sistema do <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Se você pretende usar o [emulador do HoloLens](../using-the-hololens-emulator.md), verifique se o computador também atende aos [requisitos do sistema do emulador do HoloLens](../using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Se você planeja desenvolver para headsets imersivos (VR) do HoloLens e do Windows Mixed Reality, use as recomendações e requisitos de sistema descritos na próxima seção.

> [!NOTE]
> Desenvolva e implante seus aplicativos para o HoloLens, os headsets imersivos de VR ou ambos. Verifique se você atende aos requisitos abaixo, dependendo das suas necessidades.

#### <a name="immersive-vr-headset-requirements"></a>Requisitos do headset imersivo (VR)

>[!NOTE]
>As orientações a seguir são as especificações atuais mínimas e recomendadas para seu *computador de desenvolvimento* para headset imersivo (VR) e são atualizadas regularmente.

>[!WARNING]
>Não confunda essas informações com as [diretrizes de compatibilidade mínima de hardware do computador](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que descreve as *especificações do computador do consumidor*, que é o alvo do seu jogo ou aplicativo de headset imersivo (VR).

Se seu computador de desenvolvimento de headset imersivo não tiver portas HDMI e/ou USB 3.0 padrão, você precisará de [adaptadores](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para conectar o headset.

Atualmente, há [problemas conhecidos](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) com algumas configurações de hardware, especialmente em notebooks com gráficos híbridos.

<table>
<tr>
<th></th><th> Mínimo</th><th> Recomendado</th>
</tr><tr>
<td> Processador</td><td> <b>Notebook:</b> CPU Intel Mobile Core i5 de 7ª geração, Dual-Core com Hyper Threading <b>Área de trabalho:</b> CPU Intel i5 de 6ª geração, Dual-Core com Hyper Threading <b>OU</b> equivalente a AMD FX4350 4,2Ghz Quad-Core</td><td> <b>Área de trabalho</b>: Intel i7 de 6ª geração (6 núcleos) <b>OU</b> GPU AMD Ryzen 5 1600 (6 núcleos, 12 threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> NVIDIA GTX 965M, GPU equivalente ou superior a AMD RX 460M (2GB) com capacidade DX12 <b>Computador:</b> NVIDIA GTX 960/1050, GPU equivalente ou superior a AMD Radeon RX 460 (2GB) com capacidade DX12</td><td><b>Área de trabalho</b>: NVIDIA GTX 980/1060, GPU equivalente ou superior a AMD Radeon RX 480 (2GB) com capacidade DX12</td>
</tr><tr>
<td> Versão WDDM do driver da GPU</td><td colspan="2"> Driver WDDM 2.2</td>
</tr><tr>
<td> Potência do design térmico</td><td colspan="2"> 15W ou mais</td>
</tr><tr>
<td> Portas de vídeo</td><td colspan="2"> 1 x porta de vídeo disponível para headset (HDMI 1.4 ou DisplayPort 1.2 para headsets de 60Hz, HDMI 2.0 ou DisplayPort 1.2 para headsets de 90Hz)</td>
</tr><tr>
<td> Resolução da tela</td><td colspan="2"> Resolução: SVGA (800 x 600) ou maior Profundidade de bits: 32 bits de cores por pixel</td>
</tr><tr>
<td> Memória</td><td> 8 GB de RAM ou mais</td><td> 16 GB de RAM ou mais</td>
</tr><tr>
<td> Armazenamento</td><td colspan="2"> &gt;10 GB de espaço livre adicional</td>
</tr><tr>
<td> Portas USB</td><td colspan="2"> 1 x porta USB disponível para headset (USB 3.0 Tipo A) <b>Observação: a USB deve fornecer um mínimo de 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (para conexão de acessórios)</td>
</tr>
</table>

### <a name="whats-next"></a>E agora?

> [!div class="nextstepaction"]
> [Comece sua jornada no desenvolvimento nativo](../directx-development-overview.md)


