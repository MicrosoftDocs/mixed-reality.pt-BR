## <a name="lesson-2"></a><span data-ttu-id="392d4-101">Lição 2</span><span class="sxs-lookup"><span data-stu-id="392d4-101">Lesson 2</span></span>

<span data-ttu-id="392d4-102">Na lição 2, vamos adicionar um modo Offline que nos permitirá executar a conversão de fala em texto local quando não é possível se conectar ao serviço do Azure e iremos *simular* um estado desconectado.</span><span class="sxs-lookup"><span data-stu-id="392d4-102">In Lesson 2, we will add an Offline mode that will allow us to perform local speech-to-text translation when we are unable to connect to the Azure service and we will *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="392d4-103">Selecione o objeto de "Lunarcom_Base" na hierarquia e clique em "Adicionar componente" no painel Inspetor.</span><span class="sxs-lookup"><span data-stu-id="392d4-103">Select the "Lunarcom_Base" object in the hierarchy and click “Add Component” in the inspector panel.</span></span> <span data-ttu-id="392d4-104">Pesquise e selecione o "reconhecimento Offline Lunarcom".</span><span class="sxs-lookup"><span data-stu-id="392d4-104">Search for and select the "Lunarcom Offline Recognition."</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)



2. <span data-ttu-id="392d4-106">Clique na lista suspensa no "LunarcomOfflineRecognizer" e selecione "Habilitado".</span><span class="sxs-lookup"><span data-stu-id="392d4-106">Click the dropdown in the “LunarcomOfflineRecognizer” and select “Enabled.”</span></span> <span data-ttu-id="392d4-107">Isso programará o projeto para atuar como o usuário não tem a conexão.</span><span class="sxs-lookup"><span data-stu-id="392d4-107">This will program the project to act like the user doesn't have connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="392d4-109">Agora, pressionar reproduzir no Editor do Unity e testá-lo.</span><span class="sxs-lookup"><span data-stu-id="392d4-109">Now, press play on the Unity Editor and test it.</span></span> <span data-ttu-id="392d4-110">Pressione o microfone no canto inferior esquerdo da cena e começar a falar.</span><span class="sxs-lookup"><span data-stu-id="392d4-110">Press the microphone in the bottom left hand corner in the scene and begin speaking.</span></span> 

> <span data-ttu-id="392d4-111">Observação: como estamos offline, a funcionalidade de ativação de Word foi desabilitada.</span><span class="sxs-lookup"><span data-stu-id="392d4-111">note: because we’re offline, the Wake Word functionality has been disabled.</span></span> <span data-ttu-id="392d4-112">Portanto, você terá que clique fisicamente o microfone toda vez que você deseja ter sua fala reconhecida enquanto offline.</span><span class="sxs-lookup"><span data-stu-id="392d4-112">So, you will have to physically click the microphone every time you wish to have your speech recognized while offline.</span></span> 

<span data-ttu-id="392d4-113">Abaixo está um exemplo de como poderia ser sua cena:</span><span class="sxs-lookup"><span data-stu-id="392d4-113">Below is an example of what your scene could look like:</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="392d4-115">Parabéns</span><span class="sxs-lookup"><span data-stu-id="392d4-115">Congratulations</span></span>

<span data-ttu-id="392d4-116">O modo offline foi ativado!</span><span class="sxs-lookup"><span data-stu-id="392d4-116">The offline mode has been enabled!</span></span> <span data-ttu-id="392d4-117">Agora quando você estiver longe de qualquer forma de internet, você ainda pode trabalhar em seu projeto com o Speech SDK!</span><span class="sxs-lookup"><span data-stu-id="392d4-117">Now when you're away from any form of internet, you can still work on your project with Speech-SDK!</span></span> 

[<span data-ttu-id="392d4-118">Próxima lição: SpeechSDK Lesson 3</span><span class="sxs-lookup"><span data-stu-id="392d4-118">Next Lesson: SpeechSDK Lesson 3</span></span>](link placeholder)

