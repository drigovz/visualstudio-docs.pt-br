---
title: Depuração remota de um projeto C# ou VB | Microsoft Docs
description: Saiba como depurar um aplicativo do Visual Studio C# ou Visual Basic em um computador remoto seguindo estas instruções passo a passo.
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e814e442fe740c6a5090a43a2d76fb50168ea205
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934631"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Depuração remota de um projeto em C# ou Visual Basic no Visual Studio
Para depurar um aplicativo do Visual Studio que foi implantado em um computador diferente, instale e execute as ferramentas remotas no computador em que você implantou seu aplicativo, configure seu projeto para se conectar ao computador remoto do Visual Studio e, em seguida, execute o aplicativo.

![Componentes do depurador remoto](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Para obter informações sobre a depuração remota de aplicativos do Windows universal (UWP), consulte [depurar um pacote do aplicativo instalado](debug-installed-app-package.md).

## <a name="requirements"></a>Requisitos

O depurador remoto tem suporte no Windows 7 e em versões mais recentes (não de telefone) e do Windows Server a partir do Windows Server 2008 Service Pack 2. Para obter uma lista completa dos requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Não há suporte para a depuração entre dois computadores conectados por meio de um proxy. A depuração em uma conexão de alta latência ou de baixa largura de banda, como a Internet dial-up ou pela Internet entre países, não é recomendada e pode falhar ou ser lenta de forma inaceitável.

## <a name="download-and-install-the-remote-tools"></a>Baixar e instalar as ferramentas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Em alguns cenários, pode ser mais eficiente executar o depurador remoto de um compartilhamento de arquivos. Para obter mais informações, consulte [executar o depurador remoto de um compartilhamento de arquivos](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> Configurar o depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisar adicionar permissões para usuários adicionais, altere o modo de autenticação ou o número da porta para o depurador remoto, consulte [Configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a> Depurar remotamente o projeto
O depurador não pode implantar aplicativos de área de trabalho do Visual C# ou do Visual Basic em um computador remoto, mas você ainda pode depurá-los remotamente da seguinte maneira. O procedimento a seguir pressupõe que você deseja depurá-lo em um computador chamado **MJO-DL**, conforme mostrado na ilustração a seguir.

1. Crie um projeto do WPF chamado **MyWpf**.

2. Defina um ponto de interrupção em algum lugar no código que seja facilmente acessado.

    Por exemplo, você pode definir um ponto de interrupção em um manipulador de botão. Para fazer isso, abra MainWindow. XAML e adicione um controle de botão da caixa de ferramentas e clique duas vezes no botão para abrir o manipulador.

3. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e escolha **Propriedades**.

4. Na página **Propriedades** , escolha a guia **depurar** .

    ![Captura de tela da guia Depurar no Visual Studio Gerenciador de Soluções Propriedades. A propriedade usar máquina remota está definida como ' MJO-DL: 4022 '.](../debugger/media/remotedebuggercsharp.png)

5. Verifique se a caixa de texto **diretório de trabalho** está vazia.

6. Escolha **usar computador remoto** e digite **nomeseucomputador: porta** na caixa de texto. (O número da porta é mostrado na janela do depurador remoto. O número da porta incrementa 2 em cada versão do Visual Studio).

    Neste exemplo, use:
    ::: moniker range=">=vs-2019"
    **MJO-DL: 4024** no Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL: 4022** no Visual Studio 2017
    ::: moniker-end

7. Verifique se **Habilitar depuração de código nativo** não está selecionado.

8. Compile o projeto.

9. Crie uma pasta no computador remoto que seja do mesmo caminho que a pasta de **depuração** no computador do Visual Studio: **\<source path> \MyWPF\MyWPF\bin\Debug**.

10. Copie o executável que você acabou de criar do computador do Visual Studio para a pasta recém-criada no computador remoto.

    > [!CAUTION]
    > Não faça alterações no código ou recompile (ou você deve repetir esta etapa). O executável que você copiou para o computador remoto deve corresponder exatamente à fonte local e aos símbolos.

    Você pode copiar o projeto manualmente, usar XCopy, Robocopy, PowerShell ou outras opções.

11. Verifique se o depurador remoto está em execução no computador de destino (se não for, procure o **depurador remoto** no menu **Iniciar** ). A janela do depurador remoto tem esta aparência.

     ![Captura de tela da janela do depurador remoto do Visual Studio 2017. Uma ação é listada que indica que o depurador está em execução no computador de destino.](../debugger/media/remotedebuggerwindow.png)

12. No Visual Studio, inicie a depuração (**Debug > iniciar a depuração** ou **F5**).

13. Se solicitado, insira as credenciais de rede para se conectar ao computador remoto.

     As credenciais necessárias variam de acordo com a configuração de segurança da rede. Por exemplo, em um computador de domínio, você pode inserir seu nome de domínio e senha. Em um computador que não seja de domínio, você pode inserir o nome do computador e um nome de conta de usuário válido, como <strong>MJO-DL\name@something.com</strong> , junto com a senha correta.

     Você deve ver que a janela principal do aplicativo WPF está aberta no computador remoto.

14. Se necessário, tome medidas para atingir o ponto de interrupção. Você deve ver que o ponto de interrupção está ativo. Se não estiver, os símbolos para o aplicativo não serão carregados. Tente novamente e, se isso não funcionar, obtenha informações sobre como carregar símbolos e como solucioná-los em [noções básicas sobre arquivos de símbolo e configurações de símbolo do Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. No computador do Visual Studio, você deve ver que a execução foi interrompida no ponto de interrupção.

    Se você tiver arquivos que não sejam de código que precisam ser usados pelo aplicativo, você precisará incluí-los no projeto do Visual Studio. Crie uma pasta de projeto para os arquivos adicionais (na **Gerenciador de soluções**, clique em **Adicionar > nova pasta**). Em seguida, adicione os arquivos à pasta (na **Gerenciador de soluções**, clique em **Adicionar > item existente** e selecione os arquivos). Na página **Propriedades** de cada arquivo, defina **copiar para diretório de saída** como **copiar sempre**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar a depuração com símbolos remotos

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Confira também
- [Depurando no Visual Studio](../debugger/index.yml)
- [Introdução ao depurador](../debugger/debugger-feature-tour.md)
- [Configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md)
- [Depuração remota do ASP.NET em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)