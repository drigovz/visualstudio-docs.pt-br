---
title: ASP.NET Core em um computador remoto IIS de depuração remota | Microsoft Docs
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
ms.openlocfilehash: 48c5d365c632deb4d654d5115a141ba9933d7a6f
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366874"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Depuração remota do ASP.NET Core em um computador remoto IIS no Visual Studio
Para depurar um aplicativo ASP.NET que tenha sido implantado no IIS, instalar e executar as ferramentas remotas no computador onde você implantou seu aplicativo e, em seguida, anexar a seu aplicativo em execução do Visual Studio.

![Componentes do depurador remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Este guia explica como configurar e configurar um núcleo de ASP.NET do Visual Studio, implantá-lo no IIS e anexar o depurador remoto do Visual Studio. A depuração remota ASP.NET 4.5.2, consulte [depuração remota ASP.NET em um computador com IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Você também pode implantar e depurar no IIS usando o Azure. Para o serviço de aplicativo do Azure, você pode facilmente implantar e depurar em uma instância pré-configurada do IIS e o depurador remoto usando o [depurador de instantâneo](../debugger/debug-live-azure-applications.md) ou pelo [anexando o depurador do Gerenciador de servidores](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Pré-requisitos

::: moniker range=">=vs-2019"
2019 do Visual Studio é necessário seguir as etapas mostradas neste artigo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 é necessário seguir as etapas mostradas neste artigo.
::: moniker-end

Esses procedimentos foram testados nessas configurações de servidor:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e o IIS 10

## <a name="network-requirements"></a>Requisitos de rede

Não há suporte para depuração entre dois computadores conectados por meio de um proxy. Depuração em uma alta latência ou a conexão de baixa largura de banda, como dial-up da Internet, ou pela Internet entre países não é recomendado e pode falhar ou ser muito lento. Para obter uma lista completa dos requisitos, consulte [requisitos de](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Aplicativo já em execução no IIS?

Este artigo inclui etapas sobre como configurar uma configuração básica do IIS no Windows server e implantar o aplicativo do Visual Studio. Essas etapas são incluídas para certificar-se de que o servidor tem necessário componentes instalados, que o aplicativo pode ser executado corretamente e que você está pronto para depuração remota.

* Se o aplicativo é executado no IIS e quiser apenas baixar o depurador remoto e iniciar a depuração, vá para [Baixe e instale as ferramentas remotas no Windows Server](#BKMK_msvsmon).

* Se você deseja obter ajuda para certificar-se de que seu aplicativo é configurado, implantado e executando corretamente no IIS para que você possa depurar, siga as etapas neste tópico.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Criar o aplicativo ASP.NET Core no computador do Visual Studio

1. Crie um novo Aplicativo Web ASP.NET Core. 

    ::: moniker range=">=vs-2019"
    No Visual Studio de 2019, digite **Ctrl + Q** para abrir a caixa de pesquisa, digite **asp.net**, escolha **modelos**, em seguida, escolha **criar novo aplicativo Web do ASP.NET Core** . Na caixa de diálogo que aparece, nomeie o projeto **MyASPApp**e, em seguida, escolha **criar**. Em seguida, escolha **aplicativo Web (Model-View-Controller)** e, em seguida, escolha **criar**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    No Visual Studio 2017, escolha **arquivo > Novo > projeto**, em seguida, selecione **Visual C# > Web > aplicativo Web ASP.NET Core**. Na seção de modelos do ASP.NET Core, selecione **aplicativo Web (Model-View-Controller)**. Certifique-se de que o ASP.NET Core 2.1 é selecionado, que **Habilitar suporte ao Docker** não está selecionado e que **autenticação** está definido como **sem autenticação**. Nomeie o projeto **MyASPApp**.
    ::: moniker-end

4. Abra o arquivo About.cshtml.cs e defina um ponto de interrupção na `OnGet` método (em modelos mais antigos, abra HomeController.cs em vez disso e defina o ponto de interrupção `About()` método).

## <a name="bkmk_configureIIS"></a> Instalar e configurar o IIS no Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Atualizar configurações de segurança do navegador no Windows Server

Se a configuração de segurança aprimorada estiver habilitada no Internet Explorer (ela é habilitada por padrão), em seguida, você precisa adicionar alguns domínios como sites confiáveis para que você possa baixar alguns dos componentes do servidor web. Adicione os sites confiáveis acessando **opções da Internet > Segurança > Sites confiáveis > Sites**. Adicione os domínios a seguir.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando você baixar o software, você pode receber solicitações para conceder permissão para carregar vários scripts do site da web e recursos. Alguns desses recursos não são necessárias, mas para simplificar o processo, clique em **adicionar** quando solicitado.

## <a name="install-aspnet-core-on-windows-server"></a>Instalar o ASP.NET Core no Windows Server

1. Instale o [pacote de hospedagem do Windows Server do .NET Core](https://aka.ms/dotnetcore-2-windowshosting) no sistema de hospedagem. O pacote instala o Tempo de Execução .NET Core, a Biblioteca do .NET Core e o Módulo do ASP.NET Core. Para obter mais instruções detalhadas, consulte [publicar no IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

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

1. Abra o Windows Explorer e crie uma nova pasta, **C:\Publish**, onde você irá implantar posteriormente o projeto do ASP.NET.

2. Se não ainda estiver aberto, abra o **serviços de informações da Internet (IIS) Manager**. (No painel esquerdo do Gerenciador do servidor, selecione **IIS**. Clique com o botão direito do mouse e selecione **Gerenciador do IIS (Serviços de Informações da Internet)**).

3. Sob **conexões** no painel esquerdo, vá até **Sites**.

4. Selecione o **Site padrão**, escolha **configurações básicas**e defina o **caminho físico** para **C:\Publish**.

4. Clique com botão direito do **Site padrão** nó e selecione **Adicionar aplicativo**.

5. Defina a **Alias** campo **MyASPApp**, aceite o padrão do Pool de aplicativos (**DefaultAppPool**) e defina o **caminho físico** para  **C:\Publish**.

6. Sob **conexões**, selecione **Pools de aplicativos**. Abra **DefaultAppPool** e defina o campo de pool de aplicativos como **sem código gerenciado**.

7. O novo site no Gerenciador do IIS com o botão direito, escolha **editar permissões**e certifique-se de que IUSR, IIS_IUSRS ou o usuário configurado para acesso ao aplicativo web é um usuário autorizado com direitos de leitura e execução.

    Se você não vir um desses usuários com acesso, percorra as etapas para adicionar IUSR como um usuário com direitos de leitura e execução.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publicar e implantar o aplicativo pela publicação em uma pasta local do Visual Studio

Você também pode publicar e implantar o aplicativo usando o sistema de arquivos ou outras ferramentas.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Baixe e instale as ferramentas remotas no Windows Server

Baixe a versão das ferramentas remotas que corresponde à sua versão do Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a> Configurar o depurador remoto no Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisar adicionar permissões para usuários adicionais, alterar o modo de autenticação ou número da porta para o depurador remoto, consulte [configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

Para obter informações sobre como executar o depurador remoto como um serviço, consulte [executar o depurador remoto como um serviço](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Anexar ao aplicativo ASP.NET de computador do Visual Studio

1. No computador do Visual Studio, abra a solução que você está tentando depurar (**MyASPApp** se você estiver seguindo todas as etapas neste artigo).
2. No Visual Studio, clique em **Depurar > Anexar ao processo** (Ctrl + Alt + P).

    > [!TIP]
    > No Visual Studio 2017 e versões posteriores, você pode anexar novamente o mesmo processo que você anexado anteriormente usando **Depurar > anexar novamente ao processo...** (Shift + Alt + P).

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

    * Selecione **dotnet.exe**.

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

## <a name="bkmk_openports"></a> Solução de problemas: Abra as portas necessárias no Windows Server

Na maioria das configurações, as portas necessárias estão abertas pela instalação do ASP.NET e o depurador remoto. No entanto, talvez você precise verificar se as portas estão abertas.

> [!NOTE]
> Em uma VM do Azure, você deve abrir as portas por meio de [grupo de segurança de rede](/azure/virtual-machines/windows/nsg-quickstart-portal).

Portas obrigatórias:

* 80 - obrigatórias para IIS
::: moniker range=">=vs-2019"
* 4024 - necessários para a depuração remota do Visual Studio de 2019 (consulte [as atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md) para obter mais informações).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - necessários para a depuração remota do Visual Studio 2017 (consulte [as atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md) para obter mais informações).
::: moniker-end
* UDP 3702 - porta (opcional) descoberta permite que você os **localizar** botão ao anexar ao depurador remoto no Visual Studio.

1. Para abrir uma porta no Windows Server, abra o **inicie** menu, procure **Firewall do Windows com segurança avançada**.

2. Em seguida, escolha **regras de entrada > nova regra > porta**e, em seguida, clique em **próxima**. (Para UDP 3702, escolha **regras de saída** em vez disso.)

3. Sob **portas locais específicas**, insira o número da porta, clique em **próxima**.

4. Clique em **permitir a Conexão**, clique em **próxima**.

5. Selecione um ou mais tipos de rede para habilitar para a porta e clique em **próxima**.

    O tipo selecionado deve incluir a rede à qual o computador remoto está conectado.
6. Adicione o nome (por exemplo, **IIS**, **implantação da Web**, ou **msvsmon**) para a regra de entrada e clique em **concluir**.

    Você deve ver a nova regra na lista de regras de entrada ou regras de saída.

    Se você quiser obter mais detalhes sobre como configurar o Firewall do Windows, consulte [configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Crie regras adicionais para as outras portas necessárias.
