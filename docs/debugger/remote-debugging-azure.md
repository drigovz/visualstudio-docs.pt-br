---
title: ASP.NET Core de depuração remota no IIS e no Azure | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: c6a41a332e16f79673b475404af27e540689938d
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181133"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>ASP.NET Core de depuração remota no IIS no Azure no Visual Studio

Este guia explica como configurar e configurar um aplicativo ASP.NET Core do Visual Studio, implantá-lo no IIS usando o Azure e anexar o depurador remoto do Visual Studio.

A maneira recomendada para a depuração remota no Azure depende do seu cenário:

* Para depurar ASP.NET Core no serviço Azure App, consulte [depurar aplicativos do Azure usando o depurador de instantâneos](../debugger/debug-live-azure-applications.md). Esse é o método recomendado.
* Para depurar ASP.NET Core no serviço Azure App usando recursos de depuração mais tradicionais, siga as etapas neste tópico (consulte a seção [depuração remota no serviço Azure app](#remote_debug_azure_app_service)).

    Nesse cenário, você deve implantar seu aplicativo do Visual Studio no Azure, mas não é necessário instalar ou configurar manualmente o IIS ou o depurador remoto (esses componentes são representados com linhas pontilhadas), conforme mostrado na ilustração a seguir.

    ![Componentes do depurador remoto](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Para depurar o IIS em uma VM do Azure, siga as etapas neste tópico (consulte a seção [depuração remota em uma VM do Azure](#remote_debug_azure_vm)). Isso permite que você use uma configuração personalizada do IIS, mas as etapas de instalação e implantação são mais complicadas.

    Para uma VM do Azure, você deve implantar seu aplicativo do Visual Studio no Azure e também precisa instalar manualmente a função IIS e o depurador remoto, conforme mostrado na ilustração a seguir.

    ![Componentes do depurador remoto](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Para depurar ASP.NET Core no Service Fabric do Azure, consulte [depurar um aplicativo de Service Fabric remoto](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Certifique-se de excluir os recursos do Azure criados quando você concluiu as etapas neste tutorial. Dessa forma, você pode evitar incorrer em encargos desnecessários.

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

::: moniker range=">=vs-2019"
O Visual Studio 2019 é necessário para seguir as etapas mostradas neste artigo.
::: moniker-end
::: moniker range="vs-2017"
O Visual Studio 2017 é necessário para seguir as etapas mostradas neste artigo.
::: moniker-end

### <a name="network-requirements"></a>Requisitos de rede

Não há suporte para a depuração entre dois computadores conectados por meio de um proxy. A depuração em uma conexão de alta latência ou de baixa largura de banda, como a Internet dial-up ou pela Internet entre países, não é recomendada e pode falhar ou ser lenta de forma inaceitável. Para obter uma lista completa dos requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Criar o aplicativo ASP.NET Core no computador do Visual Studio

1. Crie um novo aplicativo ASP.NET Core.

    ::: moniker range=">=vs-2019"
    No Visual Studio 2019, digite **Ctrl + Q** para abrir a caixa de pesquisa, digite **ASP.net**, escolha **modelos**e, em seguida, escolha **criar novo ASP.NET Core aplicativo Web**. Na caixa de diálogo que aparece, nomeie o projeto **MyASPApp**e, em seguida, escolha **criar**. Em seguida, escolha **aplicativo Web (Model-View-Controller)** e, em seguida, escolha **criar**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    No Visual Studio 2017, escolha **arquivo > novo projeto de >** e, em seguida, selecione **Visual C# > Web > ASP.NET Core aplicativo Web**. Na seção modelos de ASP.NET Core, selecione **aplicativo Web (Model-View-Controller)** . Certifique-se de que ASP.NET Core 2,1 está selecionado, que **habilitar o suporte ao Docker** não está selecionado e que a **autenticação** está definida como **sem autenticação**. Nomeie o projeto **MyASPApp**.
    ::: moniker-end

1. Abra o arquivo About.cshtml.cs e defina um ponto de interrupção no método `OnGet` (em modelos mais antigos, abra HomeController.cs em vez disso e defina o ponto de interrupção no método `About()`).

## <a name="remote_debug_azure_app_service"></a>ASP.NET Core de depuração remota em um serviço Azure App

No Visual Studio, você pode publicar e depurar rapidamente seu aplicativo para uma instância totalmente provisionada do IIS. No entanto, a configuração do IIS é predefinida e não é possível personalizá-la. Para obter instruções mais detalhadas, consulte [implantar um aplicativo web ASP.NET Core no Azure usando o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Se você precisar da capacidade de personalizar o IIS, tente Depurar em uma [VM do Azure](#remote_debug_azure_vm).)

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Para implantar o aplicativo e a depuração remota usando Gerenciador de Servidores

1. No Visual Studio, clique com o botão direito do mouse no nó do projeto e escolha **publicar**.

    Se você já tiver configurado anteriormente quaisquer perfis de publicação, o painel **Publicar** será exibido. Clique em **novo perfil**.

1. Escolha **Azure app serviço** na caixa de diálogo **publicar** , selecione **criar novo**e siga os prompts para publicar.

    Para obter instruções detalhadas, confira [Implantar um aplicativo Web do ASP.NET Core no Azure usando o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publicar no Serviço de Aplicativo do Azure](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Abra **Gerenciador de servidores** (**Exibir** > **Gerenciador de servidores**), clique com o botão direito do mouse na instância do serviço de aplicativo e escolha **anexar depurador**.

1. No aplicativo ASP.NET em execução, clique no link para a página **sobre** .

    O ponto de interrupção deve ser atingido no Visual Studio.

    É só isso! O restante das etapas neste tópico se aplica à depuração remota em uma VM do Azure.

## <a name="remote_debug_azure_vm"></a>ASP.NET Core de depuração remota em uma VM do Azure

Você pode criar uma VM do Azure para o Windows Server e, em seguida, instalar e configurar o IIS e os outros componentes de software necessários. Isso leva mais tempo do que a implantação em um serviço de Azure App e requer que você siga as etapas restantes neste tutorial.

Esses procedimentos foram testados nessas configurações de servidor:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>O aplicativo já está em execução no IIS na VM do Azure?

Este artigo inclui etapas sobre como configurar uma configuração básica do IIS no Windows Server e implantar o aplicativo do Visual Studio. Essas etapas estão incluídas para certificar-se de que o servidor tem os componentes necessários instalados, que o aplicativo pode ser executado corretamente e que você está pronto para depuração remota.

* Se seu aplicativo estiver em execução no IIS e você quiser apenas baixar o depurador remoto e iniciar a depuração, acesse [baixar e instalar as ferramentas remotas no Windows Server](#BKMK_msvsmon).

* Se você quiser obter ajuda para certificar-se de que seu aplicativo está configurado, implantado e em execução corretamente no IIS para que você possa depurar, siga todas as etapas neste tópico.

  * Antes de começar, siga todas as etapas descritas em [instalar e executar o IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Ao abrir a porta 80 no grupo de segurança de rede, abra também a [porta correta](#bkmk_openports) para o depurador remoto (4024 ou 4022). Dessa forma, você não precisará abri-lo mais tarde.

### <a name="update-browser-security-settings-on-windows-server"></a>Atualizar as configurações de segurança do navegador no Windows Server

Se a configuração de segurança aprimorada estiver habilitada no Internet Explorer (habilitada por padrão), talvez seja necessário adicionar alguns domínios como sites confiáveis para que você possa baixar alguns dos componentes do servidor Web. Adicione os sites confiáveis acessando **Opções da Internet > segurança > sites confiáveis > sites**. Adicione os domínios a seguir.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Ao baixar o software, você pode obter solicitações para conceder permissão para carregar vários recursos e scripts de site. Alguns desses recursos não são necessários, mas para simplificar o processo, clique em **Adicionar** quando solicitado.

### <a name="install-aspnet-core-on-windows-server"></a>Instalar o ASP.NET Core no Windows Server

1. Instale o [pacote de hospedagem do Windows Server do .NET Core](https://aka.ms/dotnetcore-2-windowshosting) no sistema de hospedagem. O pacote instalará o Runtime .NET Core, a Biblioteca do .NET Core e o Módulo do ASP.NET Core. Para obter instruções mais detalhadas, consulte [publicando no IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Se o sistema não tiver uma conexão com a Internet, obtenha e instale os *[Pacotes redistribuíveis do Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar o pacote de hospedagem do Windows Server do .NET Core.

3. Reinicie o sistema (ou execute **net stop was /y** seguido por **net start w3svc** em um prompt de comando para reconhecer uma alteração no PATH do sistema).

## <a name="choose-a-deployment-option"></a>Escolha uma opção de implantação

Se precisar de ajuda para implantar o aplicativo no IIS, considere estas opções:

* Implante criando um arquivo de configurações de publicação no IIS e importando as configurações no Visual Studio. Em alguns cenários, essa é uma maneira rápida de implantar seu aplicativo. Quando você cria o arquivo de configurações de publicação, as permissões são configuradas automaticamente no IIS.

* Implante por meio da publicação em uma pasta local e copiando a saída por um método preferencial para uma pasta de aplicativo preparada no IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Adicional Implantar usando um arquivo de configurações de publicação

Você pode usar essa opção para criar um arquivo de configurações de publicação e importá-lo para o Visual Studio.

> [!NOTE]
> Esse método de implantação usa Implantação da Web. Se desejar configurar Implantação da Web manualmente no Visual Studio em vez de importar as configurações, você poderá instalar Implantação da Web 3,6 em vez de Implantação da Web 3,6 para servidores de hospedagem. No entanto, se você configurar Implantação da Web manualmente, será necessário certificar-se de que uma pasta de aplicativo no servidor esteja configurada com os valores e permissões corretos (consulte [configurar site da ASP.net](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalar e configurar Implantação da Web para servidores de hospedagem no Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Criar o arquivo de configurações de publicação no IIS no Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar as configurações de publicação no Visual Studio e implantar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Depois que o aplicativo for implantado com êxito, ele deverá ser iniciado automaticamente. Se o aplicativo não iniciar no Visual Studio, inicie o aplicativo no IIS. Para ASP.NET Core, é necessário certificar-se de que o campo do pool de aplicativos para o **DefaultAppPool** está definido como **Sem código gerenciado**.

1. Na caixa de diálogo **configurações** , habilite a depuração clicando em **Avançar**, escolha uma configuração de **depuração** e, em seguida, escolha **remover arquivos adicionais no destino** nas opções de **publicação de arquivo** .

    > [!NOTE]
    > Se você escolher uma configuração de versão, desabilite a depuração no arquivo *Web. config* quando publicar.

1. Clique em **salvar** e Republique o aplicativo.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Adicional Implantar por publicação em uma pasta local

Você pode usar essa opção para implantar seu aplicativo se quiser copiar o aplicativo para o IIS usando o PowerShell, o RoboCopy ou desejar copiar manualmente os arquivos.

### <a name="BKMK_deploy_asp_net"></a>Configurar o site do ASP.NET Core no computador do Windows Server

Se você estiver importando configurações de publicação, poderá ignorar esta seção.

1. Abra o **Gerenciador do serviços de informações da Internet (IIS)** e vá para **sites**.

2. Clique com o botão direito do mouse no nó do **site da Web padrão** e selecione **Adicionar aplicativo**.

3. Defina o campo **alias** como **MyASPApp** e o campo pool de aplicativos como **sem código gerenciado**. Defina o **caminho físico** para **C:\Publish** (em que, posteriormente, você implantará o projeto ASP.NET Core).

4. Com o site selecionado no Gerenciador do IIS, escolha **Editar permissões**e verifique se IUSR, IIS_IUSRS ou o usuário configurado para o pool de aplicativos é um usuário autorizado com direitos de execução de leitura &.

    Se você não vir um desses usuários com acesso, siga as etapas para adicionar IUSR como um usuário com direitos de execução de leitura &.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Adicional Publicar e implantar o aplicativo publicando em uma pasta local do Visual Studio

Se você não estiver usando Implantação da Web, deverá publicar e implantar o aplicativo usando o sistema de arquivos ou outras ferramentas. Você pode começar criando um pacote usando o sistema de arquivos e, em seguida, implantar o pacote manualmente ou usar outras ferramentas, como PowerShell, RoboCopy ou XCopy. Nesta seção, presumimos que você esteja copiando o pacote manualmente se não estiver usando Implantação da Web.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a>Baixar e instalar as ferramentas remotas no Windows Server

Baixe a versão das ferramentas remotas que corresponde à sua versão do Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a>Configurar o depurador remoto no Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisar adicionar permissões para usuários adicionais, altere o modo de autenticação ou o número da porta para o depurador remoto, consulte [Configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a>Anexar ao aplicativo ASP.NET do computador do Visual Studio

1. No computador do Visual Studio, abra a solução que você está tentando depurar (**MyASPApp** se estiver seguindo as etapas neste artigo).
2. No Visual Studio, clique em **depurar > anexar ao processo** (CTRL + ALT + P).

    > [!TIP]
    > No Visual Studio 2017 e versões posteriores, você pode anexar novamente ao mesmo processo ao qual você anexou anteriormente usando **Debug > reanexar para processar...** (Shift + Alt + P).

3. Defina o campo qualificador como **\<nome do computador remoto >** e pressione **Enter**.

    Verifique se o Visual Studio adiciona a porta necessária ao nome do computador, que aparece no formato: **\<nome do computador remoto >:p classificar**

    ::: moniker range=">=vs-2019"
    No Visual Studio 2019, você deve ver **\<nome do computador remoto >: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    No Visual Studio 2017, você deve ver **\<nome do computador remoto >: 4022**
    ::: moniker-end
    A porta é necessária. Se você não vir o número da porta, adicione-o manualmente.

4. Cliquem em **Atualizar**.
    Você verá alguns processos exibidos na janela **processos disponíveis** .

    Se você não vir nenhum processo, tente usar o endereço IP em vez do nome do computador remoto (a porta é necessária). Você pode usar `ipconfig` em uma linha de comando para obter o endereço IPv4.

    Se você quiser usar o botão **Localizar** , talvez seja necessário abrir a [porta UDP 3702](#bkmk_openports) no servidor.

5. Marque **Mostrar processos de todos os usuários**.

6. Digite a primeira letra do nome do processo para localizar rapidamente seu aplicativo.

    * Selecione **dotnet. exe** (para .NET Core)

      Se você tiver vários processos mostrando **dotnet. exe**, verifique a coluna **nome de usuário** . Em alguns cenários, a coluna **nome de usuário** mostra o nome do pool de aplicativos, como o **IIS APPPOOL\DefaultAppPool**. Se você vir o pool de aplicativos, uma maneira fácil de identificar o processo correto é criar um novo pool de aplicativos nomeados para a instância do aplicativo que você deseja depurar e, em seguida, encontrá-lo facilmente na coluna **nome de usuário** .

    * Em alguns cenários do IIS, você pode encontrar o nome do aplicativo na lista de processos, como **MyASPApp. exe**. Em vez disso, você pode anexar a esse processo.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Clique em **Anexar**.

8. Abra o site do computador remoto. Em um navegador, acesse **http://\<nome do computador remoto >** .

    Você deve ver a página da Web do ASP.NET.
9. No aplicativo ASP.NET em execução, clique no link para a página **sobre** .

    O ponto de interrupção deve ser atingido no Visual Studio.

### <a name="bkmk_openports"></a>Solução de problemas Abra as portas necessárias no Windows Server

Na maioria das configurações, as portas necessárias são abertas pela instalação do ASP.NET e do depurador remoto. No entanto, se você estiver solucionando problemas de implantação e o aplicativo estiver hospedado atrás de um firewall, talvez seja necessário verificar se as portas corretas estão abertas.

Em uma VM do Azure, você deve abrir portas por meio do [grupo de segurança de rede](/azure/virtual-machines/windows/nsg-quickstart-portal).

Portas obrigatórias:

* 80-necessário para o IIS
::: moniker range=">=vs-2019"
* 4024-necessário para a depuração remota do Visual Studio 2019 (consulte [atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md) para obter mais informações).
::: moniker-end
::: moniker range="vs-2017"
* 4022-necessário para a depuração remota do Visual Studio 2017 (consulte [atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md) para obter mais informações).
::: moniker-end
* UDP 3702-a porta de descoberta (opcional) permite que você localize o botão **Localizar** ao anexar ao depurador remoto no Visual Studio.

Além disso, essas portas já devem estar abertas pela instalação do ASP.NET:
- 8172-(opcional) necessário para Implantação da Web implantar o aplicativo do Visual Studio
