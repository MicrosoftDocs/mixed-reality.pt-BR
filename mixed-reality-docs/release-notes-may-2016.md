---
title: Notas de versão – maio de 2016
description: Notas de versão do HoloLens para o Windows Holographic 2016 podem atualizar.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, notas de versão do sistema operacional, recursos, compilação, de plataforma
ms.openlocfilehash: bc4e09c36a3ab6643be1144873a624fc5ed66e37
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590737"
---
# <a name="release-notes---may-2016"></a>Notas de versão – maio de 2016

A equipe do HoloLens está comprometida em fornecer uma atualização em nosso desenvolvimento mais recente de recursos e correções de grandes porte por meio do programa Windows Insider. Graças a todas as suas sugestões, levamos seus comentários a sério. Continue a [nos enviar comentários](give-us-feedback.md) por meio do Hub de comentários, o [fóruns para desenvolvedores](https://forums.hololens.com) e [por meio do Twitter @HoloLens ](https://twitter.com/hololens).

**Versão de lançamento:** Atualização do Windows Holographic de maio de 2016 (**10.0.14342.1016**)

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

Para atualizar para a versão atual, abra o *as configurações* aplicativo, vá para *atualização e segurança*, em seguida, selecione o *verificar se há atualizações* botão.

## <a name="new-features"></a>Novos recursos

* Agora você pode **executar até três aplicativos no modo de exibição 2D simultaneamente**. Isso permite que os casos de uso infinitas de multitarefas em HoloLens. Ter o novo Hub de comentários com a lista de buscas abertas ao explorar os novos recursos nesse voo.

  ![HoloLens podem executar três aplicativos ao mesmo tempo](images/img-3625-400px.jpg)<br>
  Executar até três aplicativos no modo de exibição 2D simultaneamente

* Adicionamos novas **comandos de voz**:
   * Tente observar um holograma e girá-lo, dizendo "face para mim"
   * Alterar seu tamanho, dizendo "maior" ou "menor"
   * Mover um aplicativo dizendo "Ei Cortana, mova *nome do aplicativo* aqui."
* Fizemos **desenvolvendo em HoloLens mais fácil**. Você agora pode procurar, carregar e baixar arquivos por meio de [Windows Device Portal](using-the-windows-device-portal.md). Você pode acessar a pasta de documentos, pasta de imagens e o armazenamento local para qualquer aplicativo carregado por sideload ou implantado por meio do Visual Studio.
* O **emulador agora dá suporte a fazer logon com um Microsoft Account** exatamente como você faria em um HoloLens real. Isso pode ser habilitado no menu Ferramentas adicionais ">>".
* **Aplicativos 2D agora ocultam a barra de aplicativo e o cursor ao assistir a vídeo em tela inteira** para evitar distração. Com isso, sua experiência assistindo vídeo será ainda mais agradável no HoloLens.
* Você também pode **fixar fotos sem a barra de aplicativo** no seu mundo.

  ![A barra de aplicativo pode ser ocultada para aplicativos 2D, como fotos](images/img-3626-400px.jpg)<br>
  A barra de aplicativo pode ser ocultada para aplicativos com uma exibição 2D, como fotos
  
* **Seletor de arquivos** funciona exatamente como esperado em HoloLens.
* Atualizado **navegador Edge** para mapear a experiência do usuário unificada com área de trabalho e telefone. Habilitamos a várias instâncias do seu navegador, personalizado HoloLens nova página da guia, inspeção de guia e abra em novas janelas, junto com os aprimoramentos de desempenho e energia.
* **Groove música** aplicativo agora está em HoloLens. Visite a store para baixá-lo e tente reproduzir em segundo plano.
* Você pode personalizar facilmente como os aplicativos são organizados no seu mundo. Tente **girando seu hologramas** no ajuste o modo, basta clicar e arrastar no círculo nos wireframes verticais intermediários. Você pode notar hologramas têm **mais rigoroso ajustados caixas delimitadoras** para garantir a interação maximizada. Você também pode redimensionar todos os aplicativos simples verticalmente (exceto fotos e holograma aplicativos).

  ![Hologramas podem ser giradas depois colocá-los no mundo](images/img-3627-400px.jpg)<br>
  Girar hologramas depois colocá-los no seu mundo

* Fizemos muita **melhoria de entrada** nesse voo. Você pode conectar um mouse Bluetooth regular para HoloLens. O clicker tem sido bem ajustado para permitir o redimensionamento de & mover hologramas com um clicker. Teclado também está em execução melhor do que nunca.
* Agora você pode tomar **misto imagens realidade** , simplesmente pressionando para baixo o volume de backup + Diminuir volume simultaneamente. Você também pode compartilhar suas fotos de realidade misturada capturada & vídeos para Facebook, Twitter e YouTube.
* O comprimento máximo de gravação de **misto vídeos realidade** foi aumentado para cinco minutos.
* **Aplicativo de fotos** agora transmite vídeos do OneDrive em vez de precisar baixar o vídeo inteiro antes da reprodução.
* Melhoramos como seu **hologramas estará correto em que você os deixou**. Você também verá a opção para reconectar-se ao Wi-Fi e tente novamente se HoloLens não podem detectar de onde estiverem.
* O teclado tem um **layout aprimorado para inserir o endereço de email** com chaves que permitem que você insira o email mais popular domínios com um único clique.
* Com mais rapidez **registro de aplicativo** e **auto detecção do fuso horário** durante o OOBE, dando a você o primeiro usuário a melhor experiência.
* **Sensor de armazenamento** permite que você exiba o espaço em disco restante e usada pelo sistema e aplicativos no aplicativo configurações.
* Podemos agora são App comentários e Hub dentro de um único aplicativo **Hub de comentários** que será a ferramenta ideal para **fornecendo-nos comentários**, quais recursos você adora, quais recursos você pode fazer sem, ou quando algo que poderia ser melhor. Quando você ingressa o programa Insider, você pode manter-se em **obter as notícias mais recentes do Insider**, **taxa compilações** e vá **Jornadas de comentários** do Hub de comentários.
* Temos também [publicado de um emulador HoloLens atualizado](install-the-tools.md) compilar.
* Seus vídeos de realidade misturada agora ser melhor devido à automatic **estabilização de vídeo**.

## <a name="major-fixes"></a>Correções de grandes porte

Corrigimos os problemas com espaços holograma nos quais os espaços pode ser lenta ou incorretamente detectadas. Corrigimos um problema de desligamento que poderia continuar a tentar iniciar o shell a durante o desligamento.

Corrigimos um problema
* que bloqueia a capacidade de retomar um aplicativo XAML.
* em que uma falha deixaria uma tela preta e alguns irregulares linhas.
* rolando, às vezes, pegasse na direção errada ao usar alguns aplicativos.
* o poder LEDs pode indicar um estado desativado quando o dispositivo foi ainda em.
* Wi-Fi poderia obter desativado após sair do modo de espera.
* o provedor de identidade do Xbox oferece instalação gamertag e, em seguida, fica preso em um loop.
* o Shell falha ocasionalmente ao selecionar um arquivo baixado no seletor de arquivos do OneDrive.
* pressionando e mantendo, às vezes, em um link abre uma guia quebrada, novo e abre um menu de contexto.
* onde o portal de dispositivo do windows não permitem que os ajustes IPD de 50 80

Corrigimos os problemas com fotos onde
* uma imagem ocasionalmente exibiria girado devido a ignorar a propriedade de orientação de EXIF.
* ele poderia falhar durante a inicialização em fotos fixadas.
* vídeos seriam reiniciados depois de pausar em vez de continuar de onde pela última vez em pausa.
* reprodução de um vídeo compartilhado poderia ser evitada se ela foi compartilhada durante a reprodução.
* Gravações de capturar realidade mistas começaria com 1 de 0,5 segundo de áudio apenas do feed.
* o botão de sincronização desaparece durante a sincronização inicial do OneDrive.

Corrigimos os problemas com as configurações em que
* uma atualização era necessária quando o ambiente é alterado.
* Insira teclado não iria se comportar como clicar em Avançar em algumas caixas de diálogo.
* era difícil saber quando o clicker falha de emparelhamento.
* ele pode parar de responder com desconexão de Wi-Fi e conecte-se.

Corrigimos os problemas com o Cortana onde
* ele pode ficar presa exibindo a interface do usuário de escuta.
* perguntando "Ei Cortana, o que eu digo" de um modo exclusivo aplicativo ficará preso, se você respondeu Sim/não em vez disso, talvez a solicitação para sair do aplicativo.
* o Cortana escutar a interface do usuário não for reiniciado corretamente se você perguntar ao Cortana para ir para o modo de suspensão e, em seguida, retomar.
* as consultas "eu rede à qual estou conectado ao?" e o "Am conectei?" pode falhar quando o primeiro perfil de rede volta sem conectividade.
* a interface do usuário congela na "Listening", mas após o fechamento de um aplicativo seria imediatamente começou a fazer o reconhecimento de fala novamente.
* onde saindo do aplicativo a Cortana não permitem que você sinal de volta para ele até a reinicialização.
* ele não seria iniciar quando misto realidade captura de interface do usuário estava ativo.

Corrigimos os problemas com o Visual Studio onde
* depuração de tarefa em segundo plano não funcionou.
* análise de quadro em que o depurador de gráficos não funcionou.
* o emulador do HoloLens não apareceu na lista suspensa para o Visual Studio, a menos que TargetPlatformVersion do seu projeto foi definido como 10240.

## <a name="changes-from-previous-release"></a>Alterações de versão anterior
* O comando Cortana **Ei Cortana, reiniciar o dispositivo** não funciona. Usuário pode dizer **Ei Cortana, reinicie** ou **Ei Cortana, reinicie o dispositivo**.
* Modo de quiosque foi removido do produto.

## <a name="prior-release-notes"></a>Notas de versão prévia
* [Notas de versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte também
* [Problemas conhecidos do HoloLens](hololens-known-issues.md)
* [Instalar as ferramentas](install-the-tools.md)
* [Shell](navigating-the-windows-mixed-reality-home.md)
* [Atualizando aplicativos da UWP 2D para realidade misturada](building-2d-apps.md)
* [Acessórios de hardware](hardware-accessories.md)
* [Captura de realidade misturada](mixed-reality-capture.md)
* [Entrada de voz](voice-input.md)
* [Enviar um aplicativo para a Windows Store](submitting-an-app-to-the-microsoft-store.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
