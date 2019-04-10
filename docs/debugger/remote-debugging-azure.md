---
title: ASP.NET Core no IIS e o Azure de depuração remota | Microsoft Docs
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
ms.openlocfilehash: afed42cbdb03ba0fb47880ed0126bad9858f83fa
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59365908"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Depuração remota do ASP.NET Core no IIS no Azure no Visual Studio

Este guia explica como configurar e configurar um aplicativo de núcleo do ASP.NET do Visual Studio, implantá-lo no IIS usando o Azure e anexar o depurador remoto do Visual Studio.

A maneira recomendada para depuração remota no Azure depende de seu cenário:

* Para depurar o ASP.NET Core no serviço de aplicativo do Azure, consulte [depurar aplicativos do Azure usando o depurador de instantâneo](../debugger/debug-live-azure-applications.md). Esse é o método recomendado.
* Para depurar o ASP.NET Core no serviço de aplicativo do Azure usando os recursos de depuração mais tradicionais, siga as etapas neste tópico (consulte a seção [depuração remota no serviço de aplicativo do Azure](#remote_debug_azure_app_service)).

    Nesse cenário, você deve implantar seu aplicativo do Visual Studio para o Azure, mas não é necessário instalar manualmente ou configurar o IIS ou o depurador remoto (esses componentes são representados com linhas pontilhadas), conforme mostrado na ilustração a seguir.

    ![Componentes do depurador remoto](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Para depurar o IIS em uma VM do Azure, siga as etapas neste tópico (consulte a seção [depuração remota em uma VM do Azure](#remote_debug_azure_vm)). Isso permite que você use uma configuração personalizada do IIS, mas as etapas de instalação e implantação são mais complicadas.

    Para uma VM do Azure, você deve implantar seu aplicativo do Visual Studio para o Azure e você também precisará instalar manualmente a função do IIS e o depurador remoto, conforme mostrado na ilustração a seguir.

    ![Componentes do depurador remoto](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Para depurar o ASP.NET Core no Azure Service Fabric, consulte [depurar um aplicativo do Service Fabric remoto](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Certifique-se de excluir os recursos do Azure que você cria quando você tiver concluído as etapas neste tutorial. Dessa forma, que você pode evitar incorrer em encargos desnecessários.

## <a name="prerequisites"></a>Pré-requisitos

::: moniker range=">=vs-2019"
2019 do Visual Studio é necessário seguir as etapas mostradas neste artigo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 é necessário seguir as etapas mostradas neste artigo.
::: moniker-end

### <a name="network-requirements"></a>Requisitos de rede

Não há suporte para depuração entre dois computadores conectados por meio de um proxy. Depuração em uma alta latência ou a conexão de baixa largura de banda, como dial-up da Internet, ou pela Internet entre países não é recomendado e pode falhar ou ser muito lento. Para obter uma lista completa dos requisitos, consulte [requisitos de](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Criar o aplicativo ASP.NET Core no computador do Visual Studio

1. Crie um novo aplicativo ASP.NET Core.

    ::: moniker range=">=vs-2019"
    No Visual Studio de 2019, digite **Ctrl + Q** para abrir a caixa de pesquisa, digite **asp.net**, escolha **modelos**, em seguida, escolha **criar novo aplicativo Web do ASP.NET Core** . Na caixa de diálogo que aparece, nomeie o projeto **MyASPApp**e, em seguida, escolha **criar**. Em seguida, escolha **aplicativo Web (Model-View-Controller)** e, em seguida, escolha **criar**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    No Visual Studio 2017, escolha **arquivo > Novo > projeto**, em seguida, selecione **Visual C# > Web > aplicativo Web ASP.NET Core**. Na seção de modelos do ASP.NET Core, selecione **aplicativo Web (Model-View-Controller)**. Certifique-se de que o ASP.NET Core 2.1 é selecionado, que **Habilitar suporte ao Docker** não está selecionado e que **autenticação** está definido como **sem autenticação**. Nomeie o projeto **MyASPApp**.
    ::: moniker-end

1. Abra o arquivo About.cshtml.cs e defina um ponto de interrupção na `OnGet` método (em modelos mais antigos, abra HomeController.cs em vez disso e defina o ponto de interrupção `About()` método).

## <a name="remote_debug_azure_app_service"></a> Depuração remota do ASP.NET Core em um serviço de aplicativo do Azure

No Visual Studio, você pode publicar e depurar seu aplicativo a uma instância totalmente provisionado do IIS rapidamente. No entanto, a configuração do IIS é predefinida e não é possível personalizá-lo. Para obter instruções mais detalhadas, consulte [implantar um aplicativo web ASP.NET Core no Azure usando o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Se você precisar de capacidade de personalizar o IIS, experimente a depuração um [Azure VM](#remote_debug_azure_vm).)

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Para implantar o aplicativo e a depuração remota usando o Gerenciador de servidores

1. No Visual Studio, clique com botão direito no nó do projeto e escolha **publicar**.

    Se você já tiver configurado anteriormente quaisquer perfis de publicação, o painel **Publicar** será exibido. Clique em **novo perfil**.

1. Escolher **serviço de aplicativo do Azure** da **Publish** caixa de diálogo, selecione **criar novo**e siga os prompts para publicar.

    Para obter instruções detalhadas, confira [Implantar um aplicativo Web do ASP.NET Core no Azure usando o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publicar no Serviço de Aplicativo do Azure](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Abra **Gerenciador de servidores** (**exibição** > **Server Explorer**), clique com botão direito na instância do serviço de aplicativo e escolha **Anexar depurador**.

1. No aplicativo ASP.NET em execução, clique no link para o **sobre** página.

    O ponto de interrupção deve ser atingido no Visual Studio.

    É só isso! O restante das etapas neste tópico se aplicam a depuração remota em uma VM do Azure.

## <a name="remote_debug_azure_vm"></a> Depuração remota do ASP.NET Core em uma VM do Azure

Você pode criar uma VM do Azure para o Windows Server e, em seguida, instalar e configurar o IIS e os outros componentes de software necessárias. Isso leva mais tempo do que a implantação em um serviço de aplicativo do Azure e requer que você siga as etapas restantes neste tutorial.

Esses procedimentos foram testados nessas configurações de servidor:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e o IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Aplicativo já em execução no IIS na VM do Azure?

Este artigo inclui etapas sobre como configurar uma configuração básica do IIS no Windows server e implantar o aplicativo do Visual Studio. Essas etapas são incluídas para certificar-se de que o servidor tem os componentes necessários instalados, que o aplicativo pode ser executado corretamente e que você está pronto para depuração remota.

* Se o aplicativo é executado no IIS e quiser apenas baixar o depurador remoto e iniciar a depuração, vá para [Baixe e instale as ferramentas remotas no Windows Server](#BKMK_msvsmon).

* Se você deseja obter ajuda para certificar-se de que seu aplicativo é configurado, implantado e executando corretamente no IIS para que você possa depurar, siga as etapas neste tópico.

    * Antes de começar, siga as etapas descritas em [instalar e executar o IIS](/azure/virtual-machines/windows/quick-create-portal).

    * Quando você abre a porta 80 no grupo de segurança de rede, também abrir o [corrigir porta](#bkmk_openports) para o depurador remoto (4024 ou 4022). Dessa forma, você não precisará abri-lo mais tarde.

### <a name="update-browser-security-settings-on-windows-server"></a>Atualizar configurações de segurança do navegador no Windows Server

Se a configuração de segurança aprimorada estiver habilitada no Internet Explorer (ela é habilitada por padrão), em seguida, você precisa adicionar alguns domínios como sites confiáveis para que você possa baixar alguns dos componentes do servidor web. Adicione os sites confiáveis acessando **opções da Internet > Segurança > Sites confiáveis > Sites**. Adicione os domínios a seguir.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando você baixar o software, você pode receber solicitações para conceder permissão para carregar vários scripts do site da web e recursos. Alguns desses recursos não são necessárias, mas para simplificar o processo, clique em **adicionar** quando solicitado.

### <a name="install-aspnet-core-on-windows-server"></a>Instalar o ASP.NET Core no Windows Server

1. Instale o [pacote de hospedagem do Windows Server do .NET Core](https://aka.ms/dotnetcore-2-windowshosting) no sistema de hospedagem. O pacote instalará o Tempo de Execução .NET Core, a Biblioteca do .NET Core e o Módulo do ASP.NET Core. Para obter mais instruções detalhadas, consulte [publicar no IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Se o sistema não tiver uma conexão com a Internet, obtenha e instale os *[Pacotes redistribuíveis do Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar o pacote de hospedagem do Windows Server do .NET Core.

3. Reinicie o sistema (ou execute **net stop was /y** seguido por **net start w3svc** em um prompt de comando para reconhecer uma alteração no PATH do sistema).

## <a name="choose-a-deployment-option"></a>Escolha uma opção de implantação

Se você precisar de ajuda para implantar o aplicativo no IIS, considere estas opções:

* Implante criando um arquivo de configurações de publicação no IIS e importar as configurações no Visual Studio. Em alguns cenários, isso é uma maneira rápida de implantar seu aplicativo. Quando você cria o arquivo de configurações de publicação, permissões são automaticamente definidas no IIS.

* Implante, publicando em uma pasta local e copiar a saída por um método preferencial para uma pasta de aplicativo preparado no IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcional) Implantar usando um arquivo de configurações de publicação

Você pode usar essa opção de criar um arquivo de configurações de publicação e importe-o para o Visual Studio.

> [!NOTE]
> Esse método de implantação usa a implantação da Web. Se você quiser configurar a implantação da Web manualmente no Visual Studio em vez de importar as configurações, você pode instalar o Web implantar 3.6, em vez de Web implantar 3.6 para servidores de hospedagem. No entanto, se você configurar a implantação da Web manualmente, você precisará certificar-se de que uma pasta do aplicativo no servidor é configurada com os valores corretos e as permissões (consulte [configurar o site da Web ASP.NET](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalar e configurar a implantação da Web para hospedar servidores no Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Criar o arquivo de configurações de publicação no IIS no Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar as configurações de publicação no Visual Studio e implantar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Depois que o aplicativo for implantado com êxito, ele deverá ser iniciado automaticamente. Se o aplicativo não for iniciado do Visual Studio, inicie o aplicativo no IIS. Para ASP.NET Core, é necessário certificar-se de que o campo do pool de aplicativos para o **DefaultAppPool** está definido como **Sem código gerenciado**.

1. No **as configurações** caixa de diálogo, ative a depuração clicando **próxima**, escolha um **depurar** configuração e, em seguida, escolha **remover arquivos adicionais no destino** sob o **Publicar arquivo** opções.

    > [!NOTE]
    > Se você escolher uma configuração de versão, você desabilitar a depuração na *Web. config* arquivo quando você publicar.

1. Clique em **salvar** e, em seguida, republicar o aplicativo.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcional) Implantar pela publicação em uma pasta local

Você pode usar essa opção para implantar seu aplicativo se você deseja copiar o aplicativo para o IIS usando o Powershell, RoboCopy, ou você deseja copiar os arquivos manualmente.

### <a name="BKMK_deploy_asp_net"></a> Configurar o site da Web ASP.NET no computador com Windows Server

Se você estiver importando as configurações de publicação, você poderá ignorar esta seção.

1. Abra o **Gerenciador de serviços de informações da Internet (IIS)** e vá para **Sites**.

2. Clique com botão direito do **Site padrão** nó e selecione **Adicionar aplicativo**.

3. Defina as **Alias** campo **MyASPApp** e o campo de pool de aplicativos para **sem código gerenciado**. Defina as **caminho físico** ao **C:\Publish** (onde você irá implantar posteriormente o projeto do ASP.NET).

4. Com o site selecionado no Gerenciador do IIS, escolha **editar permissões**e certifique-se de que IUSR, IIS_IUSRS ou o usuário configurado para o Pool de aplicativos é um usuário autorizado com direitos de leitura e execução.

    Se você não vir um desses usuários com acesso, percorra as etapas para adicionar IUSR como um usuário com direitos de leitura e execução.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcional) Publicar e implantar o aplicativo pela publicação em uma pasta local do Visual Studio

Se você não estiver usando a implantação da Web, você deve publicar e implantar o aplicativo usando o sistema de arquivos ou outras ferramentas. Você pode começar criando um pacote usando o sistema de arquivos e, em seguida, implantar o pacote manualmente ou usar outras ferramentas, como XCopy, RoboCopy ou PowerShell. Nesta seção, presumimos que você estiver copiando o pacote manualmente se você não estiver usando a implantação da Web.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Baixe e instale as ferramentas remotas no Windows Server

Baixe a versão das ferramentas remotas que corresponde à sua versão do Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a> Configurar o depurador remoto no Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisar adicionar permissões para usuários adicionais, alterar o modo de autenticação ou número da porta para o depurador remoto, consulte [configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Anexar ao aplicativo ASP.NET de computador do Visual Studio

1. No computador do Visual Studio, abra a solução que você está tentando depurar (**MyASPApp** se você estiver seguindo as etapas neste artigo).
2. No Visual Studio, clique em **Depurar > Anexar ao processo** (Ctrl + Alt + P).

    > [!TIP]
    > No Visual Studio 2017 e versões posteriores, você pode anexar novamente para o mesmo processo anteriormente anexado ao usando **Depurar > anexar novamente ao processo...** (Shift + Alt + P).

3. Definir o qualificador de campo para  **\<nome do computador remoto >** e pressione **Enter**.

    Verifique se que o Visual Studio adiciona as portas necessárias para o nome do computador, que aparece no formato:  **\<nome do computador remoto >: porta**

    ::: moniker range=">=vs-2019"
    2019 do Visual Studio, você deverá ver  **\<nome do computador remoto >: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    No Visual Studio 2017, você deve ver  **\<nome do computador remoto >: 4022**
    ::: moniker-end
    A porta é necessária. Se você não vir o número da porta, adicione-o manualmente.

4. Cliquem em **Atualizar**.
    Você deve ver alguns processos que aparecem na **processos disponíveis** janela.

    Se você não vir todos os processos, tente usar o endereço IP em vez do nome do computador remoto (a porta é necessária). Você pode usar `ipconfig` em uma linha de comando para obter o endereço IPv4.

    Se você quiser usar o **encontrar** botão, talvez você precise [abra a porta UDP 3702](#bkmk_openports) no servidor.

5. Verifique **Mostrar processos de todos os usuários**.

6. Digite a primeira letra do nome do processo para localizar rapidamente o seu aplicativo.

    * Selecione **dotnet.exe** (para .NET Core)

      Se você tiver vários processos mostrando **dotnet.exe**, verifique o **nome de usuário** coluna. Em alguns cenários, o **nome de usuário** coluna mostra o nome do pool de aplicativo, tais como **IIS APPPOOL\DefaultAppPool**. Se você ver o Pool de aplicativos, é uma maneira fácil de identificar o processo correto criar um novo chamado de Pool de aplicativos para a instância do aplicativo que você deseja depurar e, em seguida, você pode encontrá-lo facilmente na **nome de usuário** coluna.

    * Em alguns cenários IIS, você pode encontrar o nome do aplicativo na lista de processos, como **MyASPApp.exe**. Você pode anexar a esse processo em vez disso.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Clique em **Anexar**.

8. Abra o site do computador remoto. Em um navegador, vá para **http://\<nome do computador remoto >**.

    Você deve ver a página da web ASP.NET.
9. No aplicativo ASP.NET em execução, clique no link para o **sobre** página.

    O ponto de interrupção deve ser atingido no Visual Studio.

### <a name="bkmk_openports"></a> Solução de problemas: Abra as portas necessárias no Windows Server

Na maioria das configurações, as portas necessárias estão abertas pela instalação do ASP.NET e o depurador remoto. No entanto, se você estiver solucionando problemas de implantação e o aplicativo é hospedado atrás de um firewall, você precisa verificar se as portas corretas estão abertas.

Em uma VM do Azure, você deve abrir as portas por meio de [grupo de segurança de rede](/azure/virtual-machines/windows/nsg-quickstart-portal).

Portas obrigatórias:

* 80 - obrigatórias para IIS
::: moniker range=">=vs-2019"
* 4024 - necessários para a depuração remota do Visual Studio de 2019 (consulte [as atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md) para obter mais informações).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - necessários para a depuração remota do Visual Studio 2017 (consulte [as atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md) para obter mais informações).
::: moniker-end
* UDP 3702 - porta (opcional) descoberta permite que você os **localizar** botão ao anexar ao depurador remoto no Visual Studio.

Além disso, essas portas já devem ser abertas pela instalação do ASP.NET:
- 8172 - (opcional) necessária para a implantação da Web para implantar o aplicativo do Visual Studio
