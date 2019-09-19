---
title: Introdução à implantação
description: Saiba mais sobre as opções de implantação de aplicativos do Visual Studio.
ms.custom: mvc
ms.date: 01/29/2019
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02e8beae03dc2828d81b80813325300fe31b3cea
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128153"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Introdução à implantação no Visual Studio

Ao implantar um aplicativo, serviço ou componente, você o distribui para instalação em outros computadores, dispositivos, servidores ou na nuvem. Você escolhe o método apropriado no Visual Studio para o tipo de implantação que deseja. (Muitos tipos de aplicativos dão suporte a outras ferramentas de implantação, como a implantação de linha de comando que não são descritas aqui.)

Confira os guias de Início Rápido e Tutoriais para obter instruções passo a passo de implantação. Para uma visão geral sobre as opções de implantação, confira [Quais opções de publicação são adequadas para mim?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Implantar na pasta local

A implantação em uma pasta local é normalmente usada para teste ou para iniciar uma implantação de teste em que outra ferramenta é usada para a implantação final.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** e **.NET Core**: Use a ferramenta Publicar para implantação em uma pasta local. As opções exatas disponíveis dependem do tipo de aplicativo. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e escolha **Publicar**. (Se você ainda não tiver configurado nenhum perfil de publicação, será necessário clicar em **Criar perfil**.) Em seguida, escolha **Pasta**. Para saber mais, confira [Implantar em uma pasta local](quickstart-deploy-to-local-folder.md).

    ![Escolha Publicar](../deployment/media/quickstart-publish.png)

- **Área de Trabalho do Windows** Você pode publicar um aplicativo de área de trabalho do Windows em uma pasta usando a implantação ClickOnce. Os usuários podem, então, instalar o aplicativo com um único clique. Para obter mais informações, confira [Implantar um aplicativo da área de trabalho usando o ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# e Visual Basic). Para C++a/CLI, consulte [implantar um aplicativo nativo usando o ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou, paraC++C/, consulte [implantar um aplicativo nativo usando um projeto de instalação](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Publicar no Azure

- **ASP.NET**, **ASP.NET Core**, **Python** e **Node.js**: Publique no Serviço de Aplicativo do Azure ou no Serviço de Aplicativo do Azure no Linux (usando contêineres) usando um dos métodos a seguir.

  - Para implantação contínua (ou automática) de aplicativos, use o Azure DevOps com [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started-yaml?view=azdevops).

  - Para implantação única (ou manual) de aplicativos, use a ferramenta **Publicar** no Visual Studio.

  Para a implantação que fornece uma configuração mais personalizada do servidor, você também pode usar a ferramenta **Publicar** para implantar aplicativos para uma máquina Virtual do Azure.

  Para usar a ferramenta **Publicar**, clique com o botão direito do mouse no Gerenciador de Soluções e escolha **Publicar**. (Se você já tiver configurado algum perfil de publicação, será necessário clicar em **Criar novo perfil**). Na caixa de diálogo Publicar, escolha **Serviço de Aplicativo** ou **Máquinas Virtuais do Azure** e, em seguida, siga as etapas de configuração.

  ![Escolher o Serviço de Aplicativo do Azure](../deployment/media/quickstart-publish-azure.png "Escolher o Serviço de Aplicativo do Azure")

  No Visual Studio 2017 versão 15.7 e posteriores, você pode implantar aplicativos ASP.NET Core no **Serviço de Aplicativo para Linux**.

  Para aplicativos do Python, confira também [Python – publicar no Serviço de Aplicativo do Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Para uma rápida introdução, confira [Publicar no Azure](quickstart-deploy-to-azure.md) e [Publicar no Linux](quickstart-deploy-to-linux.md). Confira também [Publicar um aplicativo ASP.NET Core no Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Para implantação usando o Git, confira [Implantação contínua do ASP.NET Core no Azure com o Git](/aspnet/core/publishing/azure-continuous-deployment).

  Para obter informações sobre como importar um perfil de publicação do Serviço de Aplicativo do Azure para o Visual Studio, confira [Importar configurações de publicação e implantar no Azure](../deployment/tutorial-import-publish-settings-azure.md).

  > [!NOTE]
  > Se você ainda não tem uma conta do Azure, pode [inscrever-se aqui](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Publicar na Web ou implantar em compartilhamento de rede

- **ASP.NET**, **ASP.NET Core**, **Node.js** e **Python**: Use a ferramenta Publicar para implantação em um site usando o FTP ou a Implantação da Web. Para obter mais informações, confira [Implantar um site da Web](quickstart-deploy-to-a-web-site.md).

    No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Publicar**. (Se você já tiver configurado algum perfil de publicação, será necessário clicar em **Criar novo perfil**). Na ferramenta Publicar, escolha a opção desejada e siga as etapas de configuração.

    ![Escolha IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png)

    Para obter informações sobre como importar um perfil de publicação no Visual Studio, confira [Importar configurações de publicação e implantar no IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Você também pode implantar aplicativos e serviços ASP.NET de várias outras maneiras. Para obter mais informações, confira [Implantando aplicativos e serviços Web ASP.NET](http://www.asp.net/aspnet/overview/deployment).

- **Área de Trabalho do Windows** Você pode publicar um aplicativo de área de trabalho do Windows em um servidor Web ou em um compartilhamento de arquivo de rede usando a implantação ClickOnce. Os usuários podem, então, instalar o aplicativo com um único clique. Para obter mais informações, confira [Implantar um aplicativo da área de trabalho usando o ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# e Visual Basic). Para C++a/CLI, consulte [implantar um aplicativo nativo usando o ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou, paraC++C/, consulte [implantar um aplicativo nativo usando um projeto de instalação](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-microsoft-store"></a>Publicar na Microsoft Store

No Visual Studio, você pode criar pacotes de aplicativos para implantação na Microsoft Store.

- **UWP**: Empacote o aplicativo e implante-o usando itens de menu. Para saber mais, confira [Empacotar um aplicativo UWP usando o Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Criar um pacote de aplicativo](../deployment/media/feature-tour-create-app-package.jpg)

- **Área de Trabalho do Windows**: Você pode implantar no Microsoft Store a partir do Visual Studio 2017 versão 15,4. Para fazer isso, comece criando um Projeto de Empacotamento de Aplicativos do Windows. Para obter mais informações, consulte [empacotar um aplicativo de área de trabalho para Microsoft Store](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).

    ![Empacotar um aplicativo de área de trabalho](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-net-packages-to-nugetorg"></a>Implantar pacotes .NET no NuGet.org

Para implantar código em "pacotes" que contenham código compilado (como as DLLs) e outro conteúdo necessário para projetos que consumam esses pacotes, você pode usar o Visual Studio para criar o pacote NuGet e uma ferramenta de CLI tool para emitir o comando final de implantação.

- [Criar e publicar um pacote do .NET Standard](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)
- [Criar e publicar um pacote do .NET Framework](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework)

## <a name="deploy-to-a-device-uwp"></a>Implantar em um dispositivo (UWP)

Se você estiver implantando um aplicativo UWP para testar em um dispositivo, confira [Executar aplicativos UWP em um computador remoto no Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Criar um pacote de instalador (área de trabalho do Windows)

Se precisa de uma instalação mais complexa de um aplicativo da área de trabalho do que o [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) pode oferecer, você pode criar um pacote do Windows Installer (arquivo de instalação MSI ou EXE) ou um bootstrapper personalizado.

- Um pacote de instalador baseado em MSI pode ser criado usando a [Extensão Conjunto de Ferramentas do WiX](https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset). Este é um conjunto de ferramentas de linha de comando.

   ::: moniker range=">=vs-2019"
   Para o Visual Studio 2019, obtenha a [Extensão do Conjunto de Ferramentas WiX do Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WixToolset.WixToolsetVisualStudio2019Extension).
   ::: moniker-end

- Um pacote do instalador EXE ou MSI pode ser criado usando o [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) da Flexera Software. O InstallShield pode ser usado com o Visual Studio 2017 e versões posteriores (não compatível com a Community Edition). Observe que o InstallShield Limited Edition não está mais incluído no Visual Studio e não é compatível com o Visual Studio 2017 e versões posteriores: entre em contato com a [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) para informações sobre a disponibilidade futura.

- Um pacote do instalador EXE ou MSI pode ser criado usando um projeto de instalação (vdproj). Para usar essa opção, instale a [extensão de Projetos de Instalador do Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Você também pode instalar os componentes de pré-requisitos para aplicativos de área de trabalho configurando um instalador genérico, que é conhecido como bootstrapper. Para obter mais informações, confira [Pré-requisitos de Implantação de aplicativos](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Implantar em laboratório de teste

Você pode permitir desenvolvimento e testes mais sofisticados implantando seus aplicativos em ambientes virtuais. Para obter mais informações, confira [Testar em um ambiente de laboratório](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Implantação contínua

Você pode usar Azure Pipelines para permitir a implantação contínua do seu aplicativo. Para obter mais informações, confira [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) e [Implantar no Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deploy-a-sql-database"></a>Implantar um banco de dados SQL

- [Alterar a plataforma de destino e publicar um projeto de banco de dados (SSDT (SQL Server Data Tools))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)

- [Implantar um Projeto do Analysis Services (SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)

- [Implantar projetos e pacotes do Integration Services (SSIS)](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)

- [Compilar e implantar em um banco de dados local](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Implantação de outros tipos de aplicativos

| Tipo de aplicativo | Cenário de implantação | Link |
| --- | --- | --- |
| **Aplicativo do Office** | Você pode publicar um suplemento do Office no Visual Studio. | [Implantar e publicar seu suplemento do Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Serviço WCF ou OData** | Outros aplicativos podem usar os serviços RIA WCF que você implanta em um servidor Web. | [Desenvolvendo e implantando WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | O LightSwitch não é mais compatível desde o Visual Studio 2017, mas ainda pode ser implantado no Visual Studio 2015 e anteriores. | [Implantando aplicativos LightSwitch](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você obteve uma visão geral das opções de implantação para diferentes aplicativos.

> [!div class="nextstepaction"]
> [Quais opções de publicação são adequadas para mim?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
