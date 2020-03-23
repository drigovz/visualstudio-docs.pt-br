---
title: Depuração Remota de um Projeto C++ | Microsoft Docs
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
ms.openlocfilehash: 0173ed557afa47129e0cc92d9ef9b2d94a7b198f
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302108"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Depuração Remota de um Projeto C++ no Visual Studio
Para depurar um aplicativo do Visual Studio em um computador diferente, instale e execute as ferramentas remotas no computador onde você implantará seu aplicativo, configure seu projeto para se conectar ao computador remoto do Visual Studio e, em seguida, implante e execute seu aplicativo.

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

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a>Depuração remota de um projeto C++
 No procedimento a seguir, o nome e o caminho do projeto são C:\remotetemp\MyMfc, e o nome do computador remoto é **MJO-DL**.

1. Crie um aplicativo MFC chamado **mymfc.**

2. Defina um ponto de ruptura em algum lugar da aplicação que é facilmente `CMainFrame::OnCreate`alcançado, por exemplo, em **MainFrm.cpp**, no início de .

3. No Solution Explorer, clique com o botão direito do mouse no projeto e selecione **Propriedades**. Abra a guia **Depuração.**

4. Defina o **Depurador para inicial(Depurador** **remoto do Windows)**

    ![Depuração remotaCPlus](../debugger/media/remotedebuggingcplus.png "Depuração remotaCPlus")

5. Faça as seguintes alterações nas propriedades:

   |Configuração|Valor|
   |-|-|
   |Comando remoto|C:\remotetemp\mymfc.exe|
   |Diretório de trabalho|C:\remotetemp|
   |Nome do servidor remoto|MJO-DL:*número de porta*|
   |Conexão|Remoto sem Autenticação do Windows|
   |Tipo de Depurador|Somente Nativo|
   |Diretório de implantação|C:\remotetemp.|
   |Arquivos adicionais a implantar|C:\data\mymfcdata.txt.|

    Se você implantar arquivos adicionais (opcional), a pasta deve existir em ambas as máquinas.

6. No Solution Explorer, clique com o botão direito do mouse na solução e escolha **Gerenciador de configuração**.

7. Para a configuração de **Depuração**, selecione a caixa de seleção **Implantar**.

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Iniciar a depuração **(Debug > Iniciar Depuração**ou **F5**).

9. O executável é automaticamente implantado no computador remoto.

10. Se solicitado, digite credenciais de rede para se conectar à máquina remota.

     As credenciais necessárias são específicas para a configuração de segurança da sua rede. Por exemplo, em um computador de domínio, você pode escolher um certificado de segurança ou digitar seu nome de domínio e senha. Em uma máquina não domínio, você pode inserir o nome <strong>MJO-DL\name@something.com</strong>da máquina e um nome de conta de usuário válido, como , juntamente com a senha correta.

11. No computador do Visual Studio, você deve ver que a execução está parada no ponto de ruptura.

    > [!TIP]
    > Alternativamente, você pode implantar os arquivos como um passo separado. No **Solution Explorer,** clique com o botão direito do mouse no nó **mymfc** e, em seguida, escolha **Implantar**.

    Se você tiver arquivos sem código que são exigidos pelo aplicativo, você pode especá-los em **Arquivos Adicionais para implantar** na página **Depurador remoto** do Windows.

    Alternativamente, você pode incluir os arquivos em seu projeto e definir a propriedade **Conteúdo** como **Sim** na página **Propriedades** para cada arquivo. Esses arquivos são copiados para o **Diretório de implantação** especificado na página **Depurador remoto** do Windows. Você também pode alterar o **Tipo de item** para **Arquivo de cópia** e especificar propriedades adicionais lá se precisar que os arquivos sejam copiados para uma subpasta do Diretório de **implantação**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar a depuração com símbolos remotos

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Confira também
- [Depurando no Visual Studio](../debugger/index.yml)
- [Primeiro olhe para o depurador](../debugger/debugger-feature-tour.md)
- [Configure o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Atribuições de Porta do Depurador Remoto](../debugger/remote-debugger-port-assignments.md)
- [Depuração Remota de ASP.NET em um computador remoto IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)