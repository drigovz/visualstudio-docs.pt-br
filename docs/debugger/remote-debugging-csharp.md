---
title: Depuração remota de um projeto C# ou VB | Microsoft Docs
ms.custom:
- remotedebugging"=
- seodec18
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f147acae956ad380c6e85984de29d5316394c0a
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302094"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Depuração remota de um projeto C# ou Visual Basic no Visual Studio
Para depurar um aplicativo visual studio que foi implantado em um computador diferente, instale e execute as ferramentas remotas no computador onde você implantou seu aplicativo, configure seu projeto para se conectar ao computador remoto do Visual Studio e, em seguida, execute seu aplicativo.

![Componentes de depurador remoto](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Para obter informações sobre a depuração remota de Aplicativos Universais do Windows (UWP), consulte [Debug a Installed App Package](debug-installed-app-package.md).

## <a name="requirements"></a>Requisitos

O depurador remoto é suportado no Windows 7 e nas versões mais recentes (não telefone) e do Windows Server a partir do Windows Server 2008 Service Pack 2. Para obter uma lista completa de requisitos, consulte [Requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> A depuração entre dois computadores conectados através de um proxy não é suportada. A depuração sobre uma conexão de alta latência ou baixa largura de banda, como internet dialup, ou pela Internet em todos os países não é recomendada e pode falhar ou ser inaceitávelmente lenta.

## <a name="download-and-install-the-remote-tools"></a>Baixe e instale as ferramentas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Em alguns cenários, pode ser mais eficiente executar o depurador remoto a partir de um compartilhamento de arquivos. Para obter mais informações, consulte [Executar o depurador remoto a partir de um compartilhamento de arquivos](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a>Configure o depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisar adicionar permissões para usuários adicionais, alterar o modo de autenticação ou o número da porta para o depurador remoto, consulte [Configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a>Depuração remota do projeto
O depurador não pode implantar aplicativos de desktop Visual C# ou Visual Basic em uma máquina remota, mas você ainda pode depura-los remotamente da seguinte forma. O procedimento a seguir pressupõe que você deseja depura-lo em um computador chamado **MJO-DL**, como mostrado na ilustração abaixo.

1. Crie um projeto WPF chamado **MyWpf**.

2. Defina um ponto de ruptura em algum lugar no código que é facilmente alcançado.

    Por exemplo, você pode definir um ponto de ruptura em um manipulador de botões. Para fazer isso, abra MainWindow.xaml e adicione um controle button da caixa de ferramentas e clique duas vezes no botão para abrir seu manipulador.

3. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e escolha **Propriedades**.

4. Na página **Propriedades,** escolha a guia **Depuração.**

    ![Controle remotoDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "Controle remotoDebuggerCSharp")

5. Certifique-se de que a caixa de texto **do diretório Working** está vazia.

6. Escolha **Usar máquina remota**e digitar seu nome de **máquina:porta** na caixa de texto. (O número da porta é mostrado na janela de depurador remota. O número da porta incrementa 2 em cada versão do Visual Studio).

    Neste exemplo, use:
    ::: moniker range=">=vs-2019"
    **MJO-DL:4024** no Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL:4022** no Visual Studio 2017
    ::: moniker-end

7. Certifique-se de que **a depuração de código nativo** não esteja selecionada.

8. Compile o projeto.

9. Criar uma pasta no computador remoto que é o mesmo caminho da pasta **Debug** no computador do Visual Studio: ** \<caminho de origem>\MyWPF\MyWPF\bin\Debug**.

10. Copie o executável que você acabou de construir do seu computador Visual Studio para a pasta recém-criada no computador remoto.

    > [!CAUTION]
    > Não faça alterações no código ou reconstrua (ou você deve repetir esta etapa). O executável copiado para a máquina remota deve corresponder exatamente à sua fonte e símbolos locais.

    Você pode copiar o projeto manualmente, usar Xcopy, Robocopy, Powershell ou outras opções.

11. Certifique-se de que o depurador remoto está sendo executado na máquina de destino (se não for, procure por **Depurador Remoto** no menu **Iniciar).** A janela de depurador remota se parece com isso.

     ![Janela de depurador remota](../debugger/media/remotedebuggerwindow.png "Janela de depurador remota")

12. No Visual Studio, inicie a depuração **(Debug > Start Debugging**ou **F5**).

13. Se solicitado, digite credenciais de rede para se conectar à máquina remota.

     As credenciais necessárias variam dependendo da configuração de segurança da sua rede. Por exemplo, em um computador de domínio, você pode inserir seu nome de domínio e senha. Em uma máquina não domínio, você pode inserir o nome <strong>MJO-DL\name@something.com</strong>da máquina e um nome de conta de usuário válido, como , juntamente com a senha correta.

     Você deve ver que a janela principal do aplicativo WPF está aberta no computador remoto.

14. Se necessário, tome medidas para atingir o ponto de ruptura. Você deve ver que o ponto de ruptura está ativo. Se não for, os símbolos da aplicação não foram carregados. Tente novamente, e se isso não funcionar, obtenha informações sobre o carregamento de símbolos e como soluciona-los em [Entender arquivos de símbolos e configurações de símbolos do Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. Na máquina do Visual Studio, você deve ver que a execução parou no ponto de ruptura.

    Se você tiver algum arquivo sem código que precise ser usado pelo aplicativo, você precisa incluí-los no projeto do Visual Studio. Crie uma pasta de projeto para os arquivos adicionais (no **Solution Explorer,** clique em **Adicionar > Nova Pasta**). Em seguida, adicione os arquivos à pasta (no **Solution Explorer**, clique em Adicionar **> Item existente**e selecione os arquivos). Na página **Propriedades** para cada arquivo, defina **Copiar para Diretório de saída** para copiar **sempre**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar a depuração com símbolos remotos

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Confira também
- [Depurando no Visual Studio](../debugger/index.yml)
- [Primeiro olhe para o depurador](../debugger/debugger-feature-tour.md)
- [Configure o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Atribuições de Porta do Depurador Remoto](../debugger/remote-debugger-port-assignments.md)
- [Depuração Remota de ASP.NET em um computador remoto IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)