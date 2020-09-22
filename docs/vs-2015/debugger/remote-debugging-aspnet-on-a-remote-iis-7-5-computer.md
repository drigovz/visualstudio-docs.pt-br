---
title: Depuração remota de ASP.NET em um computador remoto do IIS 7,5 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c43f392cddfd5ea36180d9b2675db82469f86ce0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838491"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Depuração remota do ASP.NET em um computador IIS remoto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode implantar um aplicativo Web ASP.NET em um computador Windows Server com o IIS e configurá-lo para depuração remota. Este guia explica como configurar e configurar um aplicativo 4.5.2 MVC do Visual Studio 2015, implantá-lo no IIS e anexar o depurador remoto do Visual Studio.

Esses procedimentos foram testados nessas configurações de servidor:
* Windows Server 2012 R2 e IIS 10
* Windows Server 2008 R2 e IIS 7,5

A maioria das informações neste artigo também se aplica à depuração remota de um aplicativo ASP.NET Core, exceto que a implantação de aplicativos do ASP.NET Core é diferente e requer etapas adicionais. Para implantar um aplicativo ASP.NET Core no IIS, será necessário concluir todas as seções deste [artigo](https://docs.asp.net/en/latest/publishing/iis.html).

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Pré-requisitos: instalar o depurador remoto no computador do Windows Server

Para obter instruções sobre como baixar o depurador remoto para o computador do Windows Server, consulte [depuração remota](../debugger/remote-debugging.md).

Para fazer a depuração remota de aplicativos ASP.NET, você pode executar o aplicativo do depurador remoto como administrador ou iniciar o depurador remoto como um serviço. Detalhes sobre como executar o depurador remoto como um serviço podem ser encontrados na [depuração remota](../debugger/remote-debugging.md).

Depois de instalado, verifique se o depurador remoto está em execução no computador de destino. (Se não for, procure o **depurador remoto** no menu **Iniciar** . ) A janela do depurador remoto tem esta aparência. (4020 é o número da porta padrão)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Criar o aplicativo no computador do Visual Studio  
  
1. Crie um novo aplicativo MVC ASP.NET. (**Arquivo/novo/projeto**e, em seguida, selecione **Visual C#/Web/ASP.NET aplicativo Web** . Na seção modelos do **ASP.NET 4.5.2** , selecione **MVC**. Verifique se o **host na nuvem** não está selecionado na seção Azure. Nomeie o projeto **MyMVC**.)
1. Abra o arquivo HomeController.cs e defina um ponto de interrupção no `About()` método.
1. Na **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e selecione **publicar**.
1. Para **selecionar um destino de publicação**, selecione **personalizado** e nomeie o perfil **MyMVC**. Clique em **Avançar**.
1. Na guia **conexão** , defina o campo **método de publicação** como **sistema de arquivos** e o campo **local de destino** como um diretório local. Clique em **Avançar**.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Defina a configuração a ser **depurada**. Clique em **Publicar**.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    O aplicativo deve ser publicado no diretório local.

## <a name="deploy-the-aspnet-application-on-the-windows-server-remote-computer"></a><a name="BKMK_deploy_asp_net"></a> Implantar o aplicativo ASP.NET no computador remoto do Windows Server

 Esta seção pressupõe que o computador com Windows Server já tem o IIS habilitado. No Windows Server 2012 R2, consulte [configuração do IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) para habilitar o IIS. (Você pode ignorar outras seções deste artigo, a menos que esteja tentando implantar um aplicativo ASP.NET Core. Para ASP.NET Core, siga as etapas no artigo para implantar o aplicativo em vez das etapas descritas aqui.)
1. Instalar o ASP.NET use os componentes da plataforma da Web para instalar o ASP.NET 4,5 (do nó do servidor no Windows Server 2012 R2, escolha **obter novos componentes da Web Platform** e, em seguida, pesquise por ASP.net)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    No Windows Server 2008 R2, instale o ASP.NET 4, em vez disso, usando este comando:   **C:\Windows\Microsoft.NET\Framework (64) \v4.0.30319\aspnet_regiis.exe-ir**
1. Copie o diretório do projeto ASP.NET do computador do Visual Studio para um diretório local (que chamaremos de **C:\Publish**) no computador do Windows Server. Você pode copiar o projeto manualmente, usar xcopy, Implantação da Web, Robocopy, PowerShell ou outras opções.

    > [!CAUTION]
    > Se precisar fazer alterações no código ou recompilar, você deverá republicar e repetir essa etapa. O executável que você copiou para o computador remoto deve corresponder exatamente à fonte local e aos símbolos.
1. Certifique-se de que o arquivo web.config liste a versão correta do .NET Framework.  Por exemplo, a versão .NET Framework instalada por padrão no Windows Server 2008 R2 é 4.0.30319, mas criamos uma versão 4.5.2 do ASP.NET. Se um aplicativo ASP.NET 4,0 estiver em execução no computador do Windows Server, você precisará alterar a versão:
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. Abra o **Gerenciador do serviços de informações da Internet (IIS)** e vá para **sites**.
1. Clique com o botão direito do mouse no nó do **site da Web padrão** e selecione **Adicionar aplicativo**.
1. Defina o campo **alias** como **MyMVC** e o campo pool de aplicativos como **ASP.NET v 4.0** (ASP.NET 4,5 não é uma opção para o pool de aplicativos). Defina o **caminho físico** para **C:\Publish** (em que você copiou o diretório do projeto ASP.net).

    >[!NOTE] 
    > Para ASP.NET Core aplicativos, defina o campo pool de aplicativos como **sem código gerenciado**.
1. Teste a implantação clicando com o botão direito do mouse em **site padrão** e selecione **procurar**.
    Se você implantou o aplicativo com êxito, verá a página da Web.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Anexar ao aplicativo ASP.NET do computador do Visual Studio

1. No computador do Visual Studio, abra a solução **MyMVC** .
1. No Visual Studio, clique em **Depurar/anexar ao processo** (**Ctrl + Alt + P**).
1. Defina o campo qualificador como ** \<remote computer name> : 4020**.
1. Clique em **Atualizar**.
    Você verá alguns processos exibidos na janela **processos disponíveis** .

    Se você não vir nenhum processo, tente usar o endereço IP em vez do nome do computador remoto (a porta é necessária). Use `ipconfig` em uma linha de comando para obter o endereço IPv4.
1. Marque  **Mostrar processos de todos os usuários**.
1. Procure **w3wp.exe** e clique em **anexar**.

     Para localizar rapidamente o nome do processo, digite a primeira letra do processo.
     
    >[!NOTE]
    > Para um aplicativo ASP.NET Core, escolha o processo de dnx.exe em vez de w3wp.exe. (Esse nome de processo pode ser alterado em uma versão futura.)

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Abra o site do computador remoto. Em um navegador, acesse **http:// \<remote computer name> **.
    
    Você deve ver a página da Web do ASP.NET.
1. Na página da Web do ASP.NET, clique no link para a página **sobre** .

    O ponto de interrupção deve ser atingido no Visual Studio.
