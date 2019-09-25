---
title: Depuração remota de um C++ projeto Visual | Microsoft Docs
ms.custom: remotedebugging
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
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 81a5ebba2d14a0e091b3b0bcd78a066ef50ed759
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211115"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>Depuração remota de um C++ projeto Visual no Visual Studio
Para depurar um aplicativo do Visual Studio em um computador diferente, instale e execute as ferramentas remotas no computador em que você implantará seu aplicativo, configure seu projeto para se conectar ao computador remoto do Visual Studio e, em seguida, implante e execute seu aplicativo.

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

## <a name="BKMK_setup"></a>Configurar o depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisar adicionar permissões para usuários adicionais, altere o modo de autenticação ou o número da porta para o depurador remoto, consulte [Configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_cplusplus"></a>Depuração remota de um C++ projeto Visual
 No procedimento a seguir, o nome e o caminho do projeto são C:\remotetemp\MyMfc e o nome do computador remoto é **MJO-DL**.

1. Crie um aplicativo MFC chamado **mymfc.**

2. Defina um ponto de interrupção em algum lugar no aplicativo que seja facilmente acessado, por exemplo, em **MainFrm. cpp**, no início de `CMainFrame::OnCreate`.

3. Em Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Propriedades**. Abra a guia **depuração** .

4. Defina o **depurador para iniciar** o **depurador remoto do Windows**.

    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. Faça as seguintes alterações nas propriedades:

   |Configuração|Valor|
   |-|-|
   |Comando remoto|C:\remotetemp\mymfc.exe|
   |Diretório de trabalho|C:\remotetemp|
   |Nome do servidor remoto|MJO-DL:*PortNumber*|
   |Conexão|Remoto sem Autenticação do Windows|
   |Tipo de Depurador|Somente Nativo|
   |Diretório de implantação|C:\remotetemp.|
   |Arquivos adicionais a implantar|C:\data\mymfcdata.txt.|

    Se você implantar arquivos adicionais (opcional), a pasta deverá existir em ambos os computadores.

6. Em Gerenciador de Soluções, clique com o botão direito do mouse na solução e escolha **Configuration Manager**.

7. Para a configuração de **Depuração**, selecione a caixa de seleção **Implantar**.

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Iniciar Depuração (**Debug > iniciar depuração**ou **F5**).

9. O executável é implantado automaticamente no computador remoto.

10. Se solicitado, insira as credenciais de rede para se conectar ao computador remoto.

     As credenciais necessárias são específicas para a configuração de segurança da sua rede. Por exemplo, em um computador de domínio, você pode escolher um certificado de segurança ou inserir seu nome de domínio e senha. Em um computador que não seja de domínio, você pode inserir o nome do computador e um nome de conta <strong>MJO-DL\name@something.com</strong>de usuário válido, como, junto com a senha correta.

11. No computador do Visual Studio, você deve ver que a execução é interrompida no ponto de interrupção.

    > [!TIP]
    > Como alternativa, você pode implantar os arquivos como uma etapa separada. Na **Gerenciador de soluções,** clique com o botão direito do mouse no nó **mymfc** e escolha **implantar**.

    Se você tiver arquivos que não são de código exigidos pelo aplicativo, poderá especificá-los em **arquivos adicionais para implantar** na página do **depurador remoto do Windows** .

    Como alternativa, você pode incluir os arquivos em seu projeto e definir a propriedade **Content** como **Sim** na página **Propriedades** de cada arquivo. Esses arquivos são copiados para o **diretório de implantação** especificado na página do **depurador remoto do Windows** . Você também pode alterar o **tipo de item** para **copiar o arquivo** e especificar propriedades adicionais ali se precisar que os arquivos sejam copiados para uma subpasta do **diretório de implantação**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar a depuração com símbolos remotos

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Consulte também
- [Depurando no Visual Studio](../debugger/index.yml)
- [Introdução ao depurador](../debugger/debugger-feature-tour.md)
- [Configurar o Firewall do Windows para Depuração Remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md)
- [Depuração Remota de ASP.NET em um computador remoto IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)