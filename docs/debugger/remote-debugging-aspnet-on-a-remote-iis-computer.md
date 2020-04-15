---
title: Depuração remota ASP.NET Núcleo em um computador IIS remoto | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: b33ead969456935dab54c042ba4fbaf1f5ff44f4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385471"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Depuração remota ASP.NET Núcleo em um computador IIS remoto no Visual Studio

Para depurar um aplicativo ASP.NET Core que foi implantado no IIS, instale e execute as ferramentas remotas no computador onde você implantou seu aplicativo e, em seguida, conecte-se ao seu aplicativo em execução do Visual Studio.

![Componentes de depurador remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Este guia explica como configurar e configurar um Visual Studio ASP.NET Core, implantá-lo no IIS e anexar o depurador remoto do Visual Studio. Para depurar remotamente ASP.NET 4.5.2, consulte [Depuração remota ASP.NET em um computador IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Você também pode implantar e depurar no IIS usando o Azure. Para o Azure App Service, você pode facilmente implantar e depurar em uma instância pré-configurada de IIS e o depurador remoto usando o [Depurador de instantâneos](../debugger/debug-live-azure-applications.md) ou [anexando o depurador do Server Explorer](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Pré-requisitos

::: moniker range=">=vs-2019"
O Visual Studio 2019 é obrigado a seguir os passos mostrados neste artigo.
::: moniker-end
::: moniker range="vs-2017"
O Visual Studio 2017 é obrigado a seguir os passos mostrados neste artigo.
::: moniker-end

Esses procedimentos foram testados nessas configurações do servidor:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

## <a name="network-requirements"></a>Requisitos de rede

A depuração entre dois computadores conectados através de um proxy não é suportada. A depuração sobre uma conexão de alta latência ou de baixa largura de banda, como internet dialup, ou pela Internet em todos os países não é recomendada e pode falhar ou ser inaceitávelmente lenta. Para obter uma lista completa de requisitos, consulte [Requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Aplicativo já rodando no IIS?

Este artigo inclui etapas para configurar uma configuração básica de IIS no servidor Windows e implantar o aplicativo no Visual Studio. Essas etapas estão incluídas para garantir que o servidor tenha componentes necessários instalados, que o aplicativo possa ser executado corretamente e que você esteja pronto para depurar remotamente.

* Se o seu aplicativo estiver em execução no IIS e você só quiser baixar o depurador remoto e começar a depurar, vá para [Baixar e Instalar as ferramentas remotas no Windows Server](#BKMK_msvsmon).

* Se você quiser ajuda para garantir que seu aplicativo esteja configurado, implantado e executado corretamente no IIS para que você possa depurar, siga todos os passos neste tópico.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Crie o aplicativo ASP.NET Core no computador do Visual Studio

1. Crie um novo Aplicativo Web ASP.NET Core. 

    ::: moniker range=">=vs-2019"
    No Visual Studio 2019, digite **Ctrl + Q** para abrir a caixa de pesquisa, digite **asp.net,** escolha **Modelos**e escolha **Criar novo ASP.NET Aplicativo Web Central**. Na caixa de diálogo que aparece, nomeie o projeto **MyASPApp**e, em seguida, escolha **Criar**. Em seguida, escolha **O Aplicativo da Web (Model-View-Controller)** e, em seguida, escolha **Criar**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    No Visual Studio 2017, escolha **Arquivo > Novo Projeto >,** em seguida, selecione Visual **C# > > Web > ASP.NET Aplicativo Web Central**. Na seção ASP.NET principais modelos, selecione **'Aplicativo da Web' (Model-View-Controller]**. Certifique-se de que ASP.NET O Core 2.1 está selecionado, que **o Suporte ao Docker** não está selecionado e que a **autenticação** está definida como **Nenhuma Autenticação**. Nomeie o projeto **MyASPApp**.
    ::: moniker-end

4. Abra o arquivo About.cshtml.cs e defina um ponto de ruptura no `OnGet` método (em `About()` modelos mais antigos, abra HomeController.cs em vez disso e defina o ponto de breakpoint no método).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Instale e configure iIS no Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Atualizar as configurações de segurança do navegador no Windows Server

Se a configuração de segurança aprimorada estiver ativada no Internet Explorer (habilitada por padrão), então você pode precisar adicionar alguns domínios como sites confiáveis para permitir que você baixe alguns dos componentes do servidor web. Adicione os sites confiáveis indo para **a Internet Opções > Segurança > Sites confiáveis > sites**. Adicione os seguintes domínios.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Ao baixar o software, você pode obter solicitações para conceder permissão para carregar vários scripts e recursos do site. Alguns desses recursos não são necessários, mas para simplificar o processo, clique **em Adicionar** quando solicitado.

## <a name="install-aspnet-core-on-windows-server"></a>Instale ASP.NET Núcleo no Windows Server

1. Instale o [pacote de hospedagem do Windows Server do .NET Core](https://aka.ms/dotnetcore-2-windowshosting) no sistema de hospedagem. O pacote instala o Runtime .NET Core, a Biblioteca do .NET Core e o Módulo do ASP.NET Core. Para obter instruções mais detalhadas, consulte [Publishing to IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Se o sistema não tiver uma conexão com a Internet, obtenha e instale os *[Pacotes redistribuíveis do Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar o pacote de hospedagem do Windows Server do .NET Core.

3. Reinicie o sistema (ou execute **a parada de rede foi /y** seguida por **net start w3svc** a partir de um prompt de comando para pegar uma alteração no PATH do sistema).

## <a name="choose-a-deployment-option"></a>Escolha uma opção de implantação

Se você precisar de ajuda para implantar o aplicativo no IIS, considere essas opções:

* Implante criando um arquivo de configurações de publicação no IIS e importando as configurações no Visual Studio. Em alguns cenários, esta é uma maneira rápida de implantar seu aplicativo. Quando você cria o arquivo de configurações de publicação, as permissões são configuradas automaticamente no IIS.

* Implante publicando em uma pasta local e copiando a saída por um método preferido para uma pasta de aplicativo preparada no IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcional) Implantar usando um arquivo de configurações de publicação

Você pode usar essa opção criar um arquivo de configurações de publicação e importá-lo para o Visual Studio.

> [!NOTE]
> Este método de implantação usa o Web Deploy. Se você quiser configurar o Web Deploy manualmente no Visual Studio em vez de importar as configurações, você pode instalar o Web Deploy 3.6 em vez do Web Deploy 3.6 para servidores de hospedagem. No entanto, se você configurar a Web Deploy manualmente, você precisará certificar-se de que uma pasta de aplicativo no servidor está configurada com os valores e permissões corretos (consulte [Configurar ASP.NET site da Web](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instale e configure o Web Deploy para servidores de hospedagem no Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Criar o arquivo de configurações de publicação no IIS no Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar as configurações de publicação no Visual Studio e implantar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Depois que o aplicativo for implantado com êxito, ele deverá ser iniciado automaticamente. Se o aplicativo não começar a partir do Visual Studio, inicie o aplicativo no IIS. Para ASP.NET Core, é necessário certificar-se de que o campo do pool de aplicativos para o **DefaultAppPool** está definido como **Sem código gerenciado**.

1. Na caixa de diálogo **Configurações,** habilite a depuração clicando **em Next**, escolha uma configuração **Debug** e, em seguida, escolha **Remover arquivos adicionais no destino** nas opções Publicar **arquivos.**

    > [!NOTE]
    > Se você escolher uma configuração Desativação, desativará a depuração no arquivo *Web.config* quando publicar.

1. Clique **em Salvar** e, em seguida, republique o aplicativo.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcional) Implantar publicando em uma pasta local

Você pode usar esta opção para implantar seu aplicativo se quiser copiar o aplicativo para IIS usando PowerShell, RoboCopy ou quiser copiar manualmente os arquivos.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Configure o site ASP.NET Core no computador do Windows Server

1. Abra o Windows Explorer e crie uma nova pasta, **C:\Publish,** onde posteriormente implantará o projeto ASP.NET Core.

2. Se ainda não estiver aberto, abra o **Gerenciador de Serviços de Informação da Internet (IIS).** (No painel esquerdo do Server Manager, selecione **IIS**. Clique com o botão direito do mouse e selecione **Gerenciador do IIS (Serviços de Informações da Internet)**).

3. Em **Conexões** no painel esquerdo, vá para **Sites**.

4. Selecione o **site padrão da Web,** escolha **Configurações básicas**e defina o caminho **físico** para **C:\Publicar**.

4. Clique com o botão direito do mouse no **nó Padrão do site** da Web e selecione Adicionar **aplicativo**.

5. Defina o campo **Alias** como **MyASPApp,** aceite o pool de aplicativos padrão **(DefaultAppPool)** e defina o **caminho físico** como **C:\Publicar**.

6. Em **Conexões,** selecione **Pools de aplicativos**. Abra **o DefaultAppPool** e defina o campo de pool de aplicativos como **Sem código gerenciado**.

7. Clique com o botão direito do mouse no novo site no IIS Manager, escolha **Editar permissões**e certifique-se de que o IUSR, IIS_IUSRS ou o usuário configurado para acesso ao aplicativo web seja um usuário autorizado com direitos de Leitura & Executar.

    Se você não ver um desses usuários com acesso, passe por etapas para adicionar iUSR como usuário com direitos de Read & Execute.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publique e implante o aplicativo publicando em uma pasta local do Visual Studio

Você também pode publicar e implantar o aplicativo usando o sistema de arquivos ou outras ferramentas.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Baixe e instale as ferramentas remotas no Windows Server

Baixe a versão das ferramentas remotas que correspondem à sua versão do Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Configure o depurador remoto no Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisar adicionar permissões para usuários adicionais, alterar o modo de autenticação ou o número da porta para o depurador remoto, consulte [Configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

Para obter informações sobre como executar o depurador remoto como um serviço, consulte [Executar o depurador remoto como um serviço](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Anexar ao aplicativo ASP.NET do computador Visual Studio

1. No computador do Visual Studio, abra a solução que você está tentando depurar (**MyASPApp** se você estiver seguindo todas as etapas deste artigo).
2. No Visual Studio, clique **em Depurar > Anexar ao Processo** (Ctrl + Alt + P).

    > [!TIP]
    > No Visual Studio 2017 e versões posteriores, você pode reconectar ao mesmo processo que você anexou anteriormente usando **Debug > Reattach to Process...** (Shift + Alt + P).

3. Defina o ** \<** campo Qualifier para o nome do computador remoto>e **pressione Enter**.

    Verifique se o Visual Studio adiciona a porta necessária ao nome do computador, que aparece no formato: ** \<nome do computador remoto>:port**

    ::: moniker range=">=vs-2019"
    No Visual Studio 2019, você deve ver ** \<o nome do computador remoto>:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    No Visual Studio 2017, você deve ver ** \<o nome do computador remoto>:4022**
    ::: moniker-end
    A porta é necessária. Se você não ver o número da porta, adicione-o manualmente.

4. Clique em **Atualizar**.
    Você deve ver alguns processos aparecerem na janela **Processos Disponíveis.**

    Se você não ver nenhum processo, tente usar o endereço IP em vez do nome do computador remoto (a porta é necessária). Você pode `ipconfig` usar em uma linha de comando para obter o endereço IPv4.

    Se você quiser usar o botão **Encontrar,** talvez seja necessário abrir a [porta UDP 3702](#bkmk_openports) no servidor.

5. Verifique **os processos do Show de todos os usuários**.

6. Digite a primeira letra do nome do seu processo para encontrar rapidamente o seu aplicativo.

    * Se estiver usando o [modelo de hospedagem no aplicativo](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models) no IIS, selecione o processo **w3wp.exe** correto. Começando no .NET Core 3, este é o padrão.

    * Caso contrário, selecione o processo **dotnet.exe.** (Este é o modelo de hospedagem fora de processo.)

    Se você tiver vários processos mostrando *w3wp.exe* ou *dotnet.exe,* verifique a coluna **Nome do Usuário.** Em alguns cenários, a coluna **Nome de Usuário** mostra o nome do pool de aplicativos, como **IIS APPPOOL\DefaultAppPool**. Se você vir o Pool de aplicativos, mas não for único, crie um novo pool de aplicativos chamado app pool para a instância do aplicativo que você deseja depurar, e então você pode encontrá-lo facilmente na coluna Nome do **Usuário.**

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Clique em **Anexar**.

8. Abra o site do computador remoto. Em um navegador, vá para **http://\<nome remoto do computador>**.

    Você deve ver a página ASP.NET web.

9. No aplicativo running ASP.NET, clique no link para a página **Sobre.**

    O ponto de ruptura deve ser atingido no Visual Studio.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Solução de problemas Abra as portas necessárias no Windows Server

Na maioria das configurações, as portas necessárias são abertas pela instalação de ASP.NET e do depurador remoto. No entanto, você pode precisar verificar se as portas estão abertas.

> [!NOTE]
> Em uma VM Azure, você deve abrir portas através do [grupo de segurança Rede](/azure/virtual-machines/windows/nsg-quickstart-portal).

Portas obrigatórias:

* 80 - Obrigatório para o IIS
::: moniker range=">=vs-2019"
* 4024 - Necessário para depuração remota do Visual Studio 2019 (consulte Atribuições de [porta de depurador remoto](../debugger/remote-debugger-port-assignments.md) para obter mais informações).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Necessário para depuração remota do Visual Studio 2017 (consulte Atribuições de [porta de depurador remoto](../debugger/remote-debugger-port-assignments.md) para obter mais informações).
::: moniker-end
* UDP 3702 - (Opcional) A porta Discovery permite que você encontre o botão **Encontrar** ao anexar ao depurador remoto no Visual Studio.

1. Para abrir uma porta no Windows Server, abra o menu **Iniciar,** procure o **Firewall do Windows com segurança avançada**.

2. Em seguida, escolha **As regras de entrada > Nova regra > Port**e clique em **"A seguir".** (Para UDP 3702, escolha **Regras de saída** em vez disso.)

3. Em **portas locais específicas,** digite o número da porta, clique **em Avançar**.

4. Clique **em Permitir a conexão,** clique em **Next**.

5. Selecione um ou mais tipos de rede para ativar a porta e clique **em Next**.

    O tipo selecionado deve incluir a rede à qual o computador remoto está conectado.
6. Adicione o nome (por exemplo, **IIS**, **Web Deploy**ou **msvsmon)** para a Regra de Entrada e clique em **Concluir**.

    Você deve ver sua nova regra na lista Regras de Entrada ou Regras de Saída.

    Se você quiser mais detalhes sobre a configuração do Firewall do Windows, consulte [Configure o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Crie regras adicionais para as outras portas necessárias.
