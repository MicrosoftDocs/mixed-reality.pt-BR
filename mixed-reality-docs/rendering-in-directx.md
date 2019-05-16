---
title: Processamento no DirectX
description: Explica a renderização holographic para Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, renderização, gráficos 3D, HolographicFrame, renderizar loop, o loop de atualização, o passo a passo, o código de exemplo
ms.openlocfilehash: 6edcaf808f2d7d48f480169e5579adb8984678a0
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629032"
---
# <a name="rendering-in-directx"></a>Processamento no DirectX

Realidade mista do Windows se baseia no DirectX para produzir rico, 3D gráfica experiências para os usuários. A abstração de renderização fica logo acima DirectX e permite que um aplicativo justificar a posição e orientação de um ou mais observadores de uma cena holográfica, previstos pelo sistema. O desenvolvedor pode, em seguida, localizar seus hologramas em relação a cada câmera, permitindo que o aplicativo renderizar essas hologramas em vários sistemas de coordenadas espaciais conforme o usuário move.

## <a name="update-for-the-current-frame"></a>Atualização para o quadro atual

Para atualizar o estado do aplicativo para hologramas, uma vez por quadro, o aplicativo irá:
* Obter um <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> do sistema de gerenciamento de exibição.
* Renderizar a cena com a previsão atual em que a visualização da câmera será quando a atualização é concluída. Observe que pode haver mais de uma câmera para a cena holográfica.

Para renderizar a modos de exibição holográfico câmera, uma vez por quadro, o aplicativo irá:
* Para cada câmera renderizar a cena do quadro atual, usando as matrizes de projeção e exibição de câmera do sistema.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Criar um novo quadro holográfico e obtenha sua previsão

O <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> tem informações de que o aplicativo precisa para atualizar e renderizar o quadro atual. O aplicativo começa a cada novo quadro chamando o **CreateNextFrame** método. Quando este método é chamado, as previsões são feitas usando os dados de sensor mais recentes disponíveis e encapsulados no **CurrentPrediction** objeto.

Um novo objeto de quadro deve ser usado para cada quadro processado conforme ele é válido somente por um instante no tempo. O **CurrentPrediction** propriedade contém informações como a posição da câmera. As informações são extrapoladas para o momento exato no tempo quando o quadro deve ser visível para o usuário.

O código a seguir foi extraído do livro **AppMain::Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>Atualizações do processo de câmera

Buffers de fundo podem alterar o quadro a quadro. Necessidades de seu aplicativo para validar o de volta do buffer para cada câmera e de versão e recriar as exibições de recursos e buffers de profundidade conforme necessário. Observe que o conjunto de poses na previsão é a lista autoritativa de câmeras que está sendo usado no quadro atual. Normalmente, você deve usar esta lista para iterar no conjunto de câmeras.

Partir **AppMain::Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

Partir **DeviceResources::EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Obter o sistema de coordenadas para usar como base para renderização

Realidade mista do Windows permite que seu aplicativo crie vários [sistemas de coordenadas](coordinate-systems-in-directx.md) conforme necessário, como o quadro de referência anexadas e o quadro estacionário de referência, que monitoram locais no mundo físico. Seu aplicativo pode usar esses sistemas de coordenadas raciocinar sobre onde a renderizar hologramas cada quadro. Ao solicitar as coordenadas de uma API, você sempre passará a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> dentro do qual você deseja que essas coordenadas sejam expressas.

Partir **AppMain::Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Esses sistemas de coordenadas, em seguida, pode ser usados para gerar as matrizes de exibição estéreo ao renderizar o conteúdo na sua cena.

Partir **CameraResources::UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Olhar de processo e o gesto de entrada

[Olhares](gaze-in-directx.md) e [mão](hands-and-motion-controllers-in-directx.md) não são baseados em tempo de entrada e, portanto, não precisa atualizar no **StepTimer** função. No entanto, essa entrada é algo que o aplicativo precisa examinar cada quadro.

### <a name="process-time-based-updates"></a>Processar atualizações baseadas em tempo

Qualquer aplicativo de renderização em tempo real precisará de alguma forma para processar atualizações com base no tempo; nós fornecemos uma maneira de fazer isso no modelo de aplicativo do Windows Holographic por meio de um **StepTimer** implementação. Isso é semelhante ao StepTimer fornecido no modelo de aplicativo de UWP do DirectX 11, portanto, se você já viu esse modelo você deverá estar na Terra familiar. A classe auxiliar StepTimer exemplo é capaz de fornecer atualizações de etapa de tempo fixas, bem como atualizações de etapa de tempo variável e o modo padrão é a variável de períodos.

No caso de renderização holográfica, especificamente escolhemos não colocar muito na função de temporizador. Isso ocorre porque você pode configurá-lo para ser uma etapa tempo fixo, caso em que ele pode ser chamado mais de uma vez por quadro – ou não, para alguns quadros – e nossas atualizações de dados holográfica devem acontecer uma vez por quadro.


Partir **AppMain::Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Posição e rotação hologramas em seu sistema de coordenadas

Se você estiver operando em um único sistema de coordenadas, assim como o modelo com o **SpatialStationaryReferenceFrame**, esse processo não é diferente da que você está caso contrário, usado para em gráficos 3D. Aqui, podemos girar o cubo e definir a matriz do modelo em relação a posição no sistema de coordenadas parado.

Partir **SpinningCubeRenderer::Update**:

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

**Nota sobre cenários avançados:** O cubo de rotação é um exemplo muito simples de como posicionar um holograma dentro de um quadro de referência único. Também é possível [usar vários SpatialCoordinateSystems](coordinate-systems-in-directx.md) no mesmo quadro renderizado, ao mesmo tempo.

### <a name="update-constant-buffer-data"></a>Atualizar dados do buffer de constantes

Transformações de modelo de conteúdo são atualizadas como de costume. Agora, você será computada transformações válidas para o sistema de coordenadas que você vai ser renderizar em.

Partir **SpinningCubeRenderer::Update**:

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

E sobre as transformações de projeção e exibição? Para obter melhores resultados, podemos desejar esperar até que quase tudo pronto para nossas chamadas de desenho antes de passarmos esses.

## <a name="render-the-current-frame"></a>Renderizar o quadro atual

Renderização no Windows Mixed Reality não é muito diferente da renderização em uma exibição mono 2D, mas há algumas diferenças que você precisa estar atento:
* Previsões de quadro holográfica são importantes. Quanto mais próximo a previsão é quando o quadro é apresentado, serão a sua hologramas melhor aparência.
* Windows Mixed Reality controla os modos de exibição da câmera. Você precisa renderizar a cada um, porque o quadro holográfico será ser apresentando-os para que você mais tarde.
* É recomendável estéreo renderização ser feito usando a instância de desenho para uma matriz de destino de renderização. O modelo de aplicativo holográfica usa a abordagem recomendada de desenho de instância para uma matriz de destino de renderização, que usa um modo de exibição de destino de renderização em um **Texture2DArray**.
* Se você deseja processar sem o uso de instanciação estéreo, você precisará criar dois não matriz RenderTargetViews (uma para cada olho) que cada referência dos dois intervalos nos **Texture2DArray** fornecido para o aplicativo do sistema. Isso não é recomendado, pois normalmente é significativamente mais lenta do que de instanciação.

### <a name="get-an-updated-holographicframe-prediction"></a>Obter uma previsão HolographicFrame atualizada

Atualizando a previsão de quadro aumenta a eficácia de estabilização da imagem e permite o posicionamento mais preciso de hologramas devido ao tempo mais curto entre a previsão e quando o quadro é visível para o usuário. Idealmente, atualize sua previsão de quadro apenas antes da renderização.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>Renderizar para cada câmera

Executar um loop no conjunto de câmera poses na previsão e renderizar em cada câmera neste conjunto.

**Configurar sua passagem de renderização**

Realidade mista do Windows usa renderização estereoscópica para aprimorar a ilusão de profundidade e renderizar stereoscopically, portanto, à esquerda e a exibição à direita são Active Directory. Com a renderização estereoscópica há um deslocamento entre as duas exibições, o cérebro pode reconciliar como profundidade real. Esta seção aborda estereoscópica renderização usando instanciamento, usando o código do modelo de aplicativo do Windows Holographic.

Cada câmera tem suas própria renderização projeção e exibição e de destino (buffer de fundo), as matrizes, no espaço de holographic. Seu aplicativo precisará criar os outros com base em câmera recursos - como o buffer de profundidade – em uma base por câmera. O modelo de aplicativo do Windows Holographic, fornecemos uma classe auxiliar para agrupar esses recursos em DX::CameraResources. Comece definindo os modos de exibição de destino de renderização:

Partir **AppMain::Render**:

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

**Use a previsão para obter as matrizes de projeção e exibição para a câmera**

As matrizes de projeção e exibição para cada câmera holográfica serão alterado em cada quadro. Atualize os dados no buffer de constantes para cada câmera holográfica. Fazer isso depois que você atualizou a previsão e antes de fazer qualquer desenho chama para essa câmera.

Partir **AppMain::Render**:

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

Aqui, mostramos como as matrizes são adquiridas do pose a câmera. Durante esse processo também obtemos o visor atual para a câmera. Observe como fornecemos um sistema de coordenadas: isso é o mesmo sistema de coordenadas são usados para entender a olhar e é o mesmo são usados para posicionar o cubo giratório.


Partir **CameraResources::UpdateViewProjectionBuffer**:

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

O visor deve ser definido de cada quadro. Seu sombreador de vértice (pelo menos) geralmente precisará ter acesso aos dados/projeção de exibição.


Partir **CameraResources::AttachViewProjectionBuffer**:

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

**Renderizar o buffer de fundo da câmera e confirmar o buffer de profundidade**:

É uma boa ideia verificar isso **TryGetViewTransform** com êxito antes de tentar usar os dados de exibição/projeção, porque se o sistema de coordenadas nao é localizável (por exemplo, rastreamento foi interrompido) seu aplicativo não é possível renderizar com ele para que quadro. O modelo só chama **renderizar** no cubo de rotação se o **CameraResources** classe indica uma atualização bem-sucedida.

Para manter hologramas onde um desenvolvedor ou um usuário coloca no mundo, Windows Mixed Reality inclui recursos para [estabilização da imagem](hologram-stability.md). Estabilização da imagem ajuda a ocultar a latência inerente em um pipeline de renderização para garantir que as experiências holográfica melhor para os usuários. um ponto de foco pode ser especificado para aprimorar ainda mais a estabilização de imagem ou um buffer de profundidade pode ser fornecido computar otimizado estabilização da imagem em tempo real.

Para obter melhores resultados, seu aplicativo deve fornecer um buffer de profundidade usando o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API. Realidade mista do Windows, em seguida, pode usar informações de geometria do buffer de profundidade para otimizar a estabilização da imagem em tempo real. O modelo de aplicativo do Windows Holographic confirma o buffer de profundidade do aplicativo por padrão, ajudando a otimizar a estabilidade holograma.

Partir **AppMain::Render**:

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
>Windows processará sua textura de profundidade na GPU, portanto, deve ser possível usar seu buffer de profundidade como um recurso de sombreador. O ID3D11Texture2D que você criar deve estar em um formato sem especificação de tipo e deve estar associado como um modo de exibição de recurso do sombreador. Aqui está um exemplo de como criar uma textura de profundidade que pode ser confirmada para a estabilização da imagem.

Código para o **criação de recursos de buffer de profundidade para CommitDirect3D11DepthBuffer**:

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

**Desenhar conteúdo holográfico**

O modelo de aplicativo do Windows Holographic renderiza o conteúdo em estéreo, usando a técnica recomendada da instância de geometria de desenho para uma Texture2DArray de tamanho 2. Vamos examinar a instanciação parte dessa situação, e como ele funciona no Windows Mixed Reality.

Partir **SpinningCubeRenderer::Render**:

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

Cada instância acessa uma matriz de projeção/de exibição diferente do buffer constante. Aqui está a estrutura de buffer de constantes, que é apenas uma matriz de matrizes de 2.

Partir **VertexShaderShared.hlsl**, incluído por **VPRTVertexShader.hlsl**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

O índice de matriz de destino de renderização deve ser definido para cada pixel. No trecho a seguir, output.viewId é mapeado para o **SV_RenderTargetArrayIndex** semântica. Observe que isso requer suporte para um recurso opcional do Direct3D 11.3, que permite que o índice de matriz de destino de renderização semântica seja definida de qualquer estágio de sombreador.

From **VPRTVertexShader.hlsl**:

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

Partir **VertexShaderShared.hlsl**, incluído por **VPRTVertexShader.hlsl**:

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

Se você quiser usar a instância existente, técnicas de desenho com esse método de desenho para um aparelho de som renderizam a matriz de destino, tudo o que você precisa fazer é desenhar duas vezes o número de instâncias que você normalmente precisa. No sombreador, divida **input.instId** por 2 para obter a ID da instância original, que podem ser indexadas em (por exemplo) em um buffer de dados por objeto: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Observação importante sobre como renderizar conteúdo estéreo em HoloLens

Realidade mista do Windows oferece suporte a capacidade de definir o índice de matriz de destino de renderização de qualquer estágio de sombreador; Normalmente, essa é uma tarefa que só pode ser feita no estágio de sombreador de geometria devido à maneira como a semântica é definida para o Direct3D 11. Aqui, mostramos um exemplo completo de como configurar um pipeline de renderização com apenas o conjunto de estágios de pixel e vértice sombreador. O código de sombreador é conforme descrito acima.

Partir **SpinningCubeRenderer::Render**:

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Observação importante sobre como renderizar em dispositivos não HoloLens

A definição de índice da matriz de destino de renderização no sombreador de vértice requer que o driver de gráficos oferece suporte a um recurso opcional do Direct3D 11.3, que oferece suporte a HoloLens. Seu aplicativo pode ser capaz de implementar com segurança apenas essa técnica para renderização e todos os requisitos para execução em que o Microsoft HoloLens.

Ele pode ser o caso em que você deseja usar o emulador de HoloLens, bem, o que pode ser uma ferramenta de desenvolvimento avançado para seu aplicativo holográfica – e dar suporte a dispositivos de fone de ouvido imersivo Windows Mixed Reality anexados a computadores com Windows 10. Suporte para o caminho de renderização não HoloLens - e, portanto, para todos os Windows Mixed Reality - também é criado no modelo de aplicativo do Windows Holographic. O código de modelo, você encontrará o código para habilitar seu aplicativo holográfico seja executado no GPU no seu computador de desenvolvimento. Aqui está como o **DeviceResources** classe procura esse suporte de recurso opcional.

Partir **DeviceResources::CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Para dar suporte à renderização sem esse recurso opcional, seu aplicativo deve usar um sombreador de geometria para definir o índice de matriz de destino de renderização. Este trecho de código seria adicionado *após* **VSSetConstantBuffers**, e *antes* **PSSetShader** no exemplo de código mostrado anteriormente na seção que explica como renderizar estéreo em HoloLens.

Partir **SpinningCubeRenderer::Render**:

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

**OBSERVAÇÃO DE HLSL**: Nesse caso, você também deve carregar um sombreador de vértice ligeiramente modificada que passa o índice de matriz de destino de renderização para o sombreador de geometria usando uma semântica, como TEXCOORD0 de sombreador sempre permitidos. O sombreador de geometria não tem que fazer qualquer trabalho; o sombreador de geometria do modelo passa por todos os dados, exceto o índice de matriz de destino de renderização, que é usado para definir o SV_RenderTargetArrayIndex semântica.

Código de modelo de aplicativo do **GeometryShader.hlsl**:

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a>Apresentar

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Habilitar o quadro holographic apresentar a cadeia de troca

Com o Windows Mixed Reality, o sistema controla a cadeia de troca. O sistema, em seguida, gerencia os quadros de apresentação para cada câmera holographic para garantir uma experiência de usuário de alta qualidade. Ele também fornece uma atualização do visor em cada quadro, para cada câmera, para otimizar os aspectos do sistema, como a estabilização da imagem ou a captura de realidade mista. Portanto, um aplicativo holográfico usando o DirectX não chama **presente** corrente de troca um DXGI. Em vez disso, você usa o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> classe apresentar todas as cadeias de permuta para um quadro quando você terminar desenhá-la.

Partir **DeviceResources::Present**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

Por padrão, essa API aguarda o quadro concluir antes de retornar. Aplicativos holográfico devem aguardar o quadro anterior seja concluída antes de começar a trabalhar em um novo quadro, porque isso reduz a latência e permite que para obter melhores resultados de previsões de quadro holográfica. Isso não é uma regra de disco rígida e, se você tiver quadros que demoram mais do que a atualização de uma tela para renderizar, você podem desabilitar essa espera, passando o parâmetro HolographicFramePresentWaitBehavior <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>. Nesse caso, você usaria provavelmente um thread de renderização assíncrona para manter uma carga contínua na GPU. Observe que a taxa de atualização do dispositivo HoloLens é 60hz, em que um quadro tem uma duração de aproximadamente 16 ms. Dispositivos de fone de ouvido imersivo podem variar de 60hz a 90hz; ao atualizar a exibição a 90 hz, cada quadro terá uma duração de aproximadamente 11 ms.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>Lidar com cenários de DeviceLost em cooperação com o HolographicFrame

Aplicativos DirectX 11 geralmente deseja verificar o HRESULT retornado pela cadeia de troca DXGI **presente** função para descobrir se houve uma **DeviceLost** erro. O <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> classe manipula isso para você. Inspecione o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> retorna para descobrir se você precisa liberar e recriar o dispositivo Direct3D e os recursos com base em dispositivo.

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

Observe que, se o dispositivo Direct3D foi perdido e você recriá-lo, você precisa informar o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> para começar a usar o novo dispositivo. A cadeia de troca será recriada para este dispositivo.

Partir **DeviceResources::InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

Depois que o quadro é apresentado, você pode retornar para o loop de programa principal e permitir que ele continue para o próximo quadro.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>PCs de elementos gráficos híbridos e aplicativos de realidade misturada

Windows 10 Creators Update PCs podem ser configurados com **ambos** discretos e integradas de GPUs. Com esses tipos de computadores, o Windows escolherá o fone de ouvido está conectado ao adaptador. Aplicativos devem garantir que o dispositivo DirectX cria usa o mesmo adaptador.

Código de exemplo mais geral do Direct3D demonstra como criar um dispositivo DirectX usando o adaptador de hardware padrão, que, em um sistema híbrido pode não ser o mesmo que aquele usado para o fone de ouvido.

Para contornar isso pode causar problemas, use o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> partir <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId() ou <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId(). Este IdentificaçãoDoAdaptador, em seguida, pode ser usado para selecionar o direito DXGIAdapter usando IDXGIFactory4.EnumAdapterByLuid.

Partir **DeviceResources::InitializeUsingHolographicSpace**:

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

Código para **atualizar DeviceResources::CreateDeviceResources para usar IDXGIAdapter**

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

**Gráficos híbridos e Media Foundation**

Usar o Media Foundation em sistemas híbrida pode causar problemas em que o vídeo não será renderizado ou textura de vídeo está corrompida. Isso pode ocorrer porque o Media Foundation é padronizar para um comportamento do sistema conforme mencionado acima. Em alguns cenários, é necessário para suporte a multithreading e a criação correta sinalizadores são definidos como criar um ID3D11Device separado.

Ao inicializar o ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT sinalizador deve ser definido como parte do D3D11_CREATE_DEVICE_FLAG. Depois que o dispositivo e o contexto é criado, chame <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> para habilitar multithreading. Para associar o dispositivo com o <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use o <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> função.

Código para **associar um ID3D11Device IMFDXGIDeviceManager**:

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a>Consulte também
* [Sistemas de coordenadas no DirectX](coordinate-systems-in-directx.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
