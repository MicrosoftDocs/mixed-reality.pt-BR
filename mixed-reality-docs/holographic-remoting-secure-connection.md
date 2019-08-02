---
title: Estabelecendo uma conexão segura com o Holographic Remoting
description: Esta página explica como estabelecer uma conexão segura criptografada ao usar a comunicação remota do Holographic.
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: 5bc039d7a1e500f577c4a30d2d082b718a45a8b4
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718070"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Estabelecendo uma conexão segura com o Holographic Remoting

>[!IMPORTANT]
>Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.

Esta página explica como estabelecer uma conexão segura criptografada ao usar a comunicação remota do Holographic.

Ao transmitir conteúdo para o HoloLens 2 em uma rede insegura, como uma Wi-Fi aberta ou a Internet, é altamente recomendável usar uma conexão criptografada.

>[!IMPORTANT]
>Mesmo ao usar um WiFi local confiável usando uma conexão criptografada deve ser considerado.

Para poder usar uma conexão criptografada, você precisará implementar um [player personalizado](holographic-remoting-create-player.md) e um [aplicativo host personalizado](holographic-remoting-create-host.md).

A criptografia é obtida usando a implementação de TLS de plataformas subjacentes.

## <a name="basics-of-an-encrypted-connection"></a>Noções básicas de uma conexão criptografada

Os objetos a seguir precisam ser implementados para permitir uma troca de certificado.

>[!TIP]
>A implementação de interfaces do WinRT pode ser C++feita facilmente usando/WinRT. O capítulo [criar APIs C++com/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/author-apis) descreve isso em detalhes.

>[!IMPORTANT]
>O ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` dentro do pacote NuGet contém documentação detalhada para a API relacionada a conexões seguras.

1) Um objeto de certificado, que precisa implementar a ```ICertificate``` interface.

    * Retornar o conteúdo binário do certificado pfx por meio do ```GetCertificatePfx``` método. O mesmo que o conteúdo binário de um arquivo. pfx.
    * Retornar o nome da entidade do ```GetSubjectName```certificado por meio de.
    * Retornar a senha pfx por ```GetPfxPassword```meio de. Retornar uma cadeia de caracteres vazia para um pfx desprotegido.

2) Um provedor de certificados que ```ICertificateProvider``` implementa a interface que fornece um certificado quando solicitado ```GetCertificate``` pelo método.

3) Um validador de certificado ```ICertificateValidator``` que implementa a interface. Sua tarefa é verificar os certificados de entrada.
    * O ```PerformSystemValidation``` método deve retornar ```true``` quando a plataforma subjacente deve validar a cadeia de certificados de ```false``` entrada, caso contrário.
    * ```ValidateCertificate```é chamado pelo contexto do cliente para solicitar a validação de um certificado. Esse método aceita a cadeia de certificados (com o primeiro certificado sendo o certificado da entidade), o nome do servidor com o qual a conexão está sendo estabelecida e se uma verificação de revogação deve ser forçada. O resultado da validação do sistema será fornecido se a validação do sistema subjacente tiver sido solicitada. Para continuar o ```CertificateValidated``` processamento com o resultado apropriado ou ```Cancel``` para cancelar, a validação precisa ser chamada no passado ```ICertificateValidationCallback```.

Além disso, para permitir a troca de um token seguro, os objetos a seguir precisam ser implementados.

1) Um provedor de autenticação que ```IAuthenticationProvider``` implementa a interface. Seu ```GetToken``` método é chamado pelo contexto do cliente para solicitar um token para autenticação de cliente. Para continuar ```TokenReceived``` a fornecer o token de autenticação e continuar o processo de conexão ```Cancel``` ou para cancelar, o processo precisa ser chamado no passado ```IAuthenticationProviderCallback```.
2) Um receptor de autenticação que ```IAuthenticationReceiver``` implementa a interface. Sua tarefa é validar tokens de entrada.
    * O ```GetRealm``` método deve retornar o nome do realm de autenticação.
    * O ```ValidateToken``` método é chamado pelo contexto de rede do servidor para solicitar a validação de um token de autenticação de cliente. Para continuar a chamada ```ValidationCompleted``` para a conclusão do sinal da validação ```Cancel``` ou para rejeitar a conexão do cliente. A conexão do cliente será admitida ou rejeitada com base no resultado da ```ValidationCompleted```validação passado para. 

Depois que esses objetos são ```ListenSecure``` implementados precisam ser chamados em ```Listen``` vez ```ConnectSecure``` de e ```Connect``` em vez de no contexto remoto e no contexto do Player, respectivamente. ```ListenSecure```requer um provedor de certificado adicional e receptor de ```Listen```autenticação sobre o. ```ConnectSecure```requer um provedor de autenticação adicional e um validador ```Connect```de certificado.

## <a name="see-also"></a>Consulte também
* [Escrevendo um aplicativo de host de comunicação remota do Holographic](holographic-remoting-create-host.md)
* [Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado](holographic-remoting-create-player.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota Holographic](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)