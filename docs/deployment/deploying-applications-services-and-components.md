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
ms.openlocfilehash: 2be42b3a66f6bd874568945081972b220e7a7830
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006556"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Introdução à implantação no Visual Studio

Ao implantar um aplicativo, serviço ou componente, você o distribui para instalação em outros computadores, dispositivos, servidores ou na nuvem. Você escolhe o método apropriado no Visual Studio para o tipo de implantação que deseja. (Muitos tipos de aplicativos dão suporte a outras ferramentas de implantação, como a implantação de linha de comando ou NuGet, que não são descritas aqui.)

Confira os guias de início rápido e os tutoriais para obter instruções de implantação passo a passo. Para uma visão geral sobre as opções de implantação, confira [Quais opções de publicação são adequadas para mim?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-a-local-folder"></a>Implantar em uma pasta local

A implantação em uma pasta local normalmente é usada para teste ou para iniciar uma implantação em etapas na qual outra ferramenta é usada para implantação final.

- **ASP.net**, **ASP.NET Core**, **Node.js**, **Python** e. **Net Core**: Use a ferramenta de **publicação** para implantar em uma pasta local. As opções exatas disponíveis dependem do tipo de aplicativo. No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Publicar**. (Se você ainda não tiver configurado perfis de publicação, deverá selecionar **criar novo perfil**.) Em seguida, selecione **pasta**. Para saber mais, confira [Implantar em uma pasta local](quickstart-deploy-to-local-folder.md).

    ![Captura de tela que mostra a seleção de publicar.](../deployment/media/quickstart-publish.png)

- **Área de trabalho do Windows**: você pode publicar um aplicativo de área de trabalho do Windows em uma pasta usando a implantação do ClickOnce. Os usuários podem, então, instalar o aplicativo com um único clique. Para obter mais informações, consulte os seguintes artigos:

  - [Implante um .NET Framework aplicativo de área de trabalho do Windows usando o ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md).
  - [Implante um aplicativo de área de trabalho do Windows .NET usando o ClickOnce](quickstart-deploy-using-clickonce-folder.md).
  - [Implantar um aplicativo C++/CLR usando o ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou, para C/C++, consulte [implantar um aplicativo nativo usando um projeto de instalação](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Publicar no Azure

- **ASP.net**, **ASP.NET Core**, **Python** e **Node.js**: publicar no serviço de Azure app ou serviço de Azure app no Linux (usando contêineres) usando um dos seguintes métodos:

  - Para implantação contínua (ou automática) de aplicativos, use o Azure DevOps com [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).
  - Para implantação única (ou manual) de aplicativos, use a ferramenta **Publicar** no Visual Studio.

  Para implantação que fornece mais configuração personalizada do servidor, você também pode usar a ferramenta de **publicação** para implantar aplicativos em uma máquina virtual do Azure.

  Para usar a ferramenta de **publicação** , clique com o botão direito do mouse no projeto no Gerenciador de soluções e selecione **publicar**. (Se você tiver configurado anteriormente todos os perfis de publicação, deverá selecionar **criar novo perfil**.) Na caixa de diálogo **publicar** , selecione **serviço de aplicativo** ou **máquinas virtuais do Azure** e siga as etapas de configuração.

  ![Captura de tela que mostra a seleção de Azure App serviço.](../deployment/media/quickstart-publish-azure-new.png "Escolher serviço de Azure App")

  A partir do Visual Studio 2017 versão 15,7, você pode implantar ASP.NET Core aplicativos no serviço de aplicativo no Linux.

  Para aplicativos do Python, confira também [Python – publicar no Serviço de Aplicativo do Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Para uma rápida introdução, confira [Publicar no Azure](quickstart-deploy-to-azure.md) e [Publicar no Linux](quickstart-deploy-to-linux.md). Confira também [Publicar um aplicativo ASP.NET Core no Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Para implantação usando o Git, confira [Implantação contínua do ASP.NET Core no Azure com o Git](/aspnet/core/publishing/azure-continuous-deployment).

  > [!NOTE]
  > Se você ainda não tiver uma conta do Azure, poderá [se inscrever aqui](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-the-web-or-deploy-to-a-network-share"></a>Publicar na Web ou implantar em um compartilhamento de rede

- **ASP.net**, **ASP.NET Core**, **Node.js** e **Python**: você pode usar a ferramenta de **publicação** para implantar em um site usando FTP ou implantação da Web. Para obter mais informações, consulte [implantar em um site](quickstart-deploy-to-a-web-site.md).

    Em Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **publicar**. (Se você tiver configurado anteriormente todos os perfis de publicação, deverá selecionar **criar novo perfil**.) Na ferramenta de **publicação** , selecione a opção desejada e siga as etapas de configuração.

    ![Captura de tela que mostra a seleção do IIS.](../deployment/media/quickstart-publish-iis.png)

    Para obter informações sobre como importar um perfil de publicação no Visual Studio, confira [Importar configurações de publicação e implantar no IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Você também pode implantar aplicativos e serviços ASP.NET de várias outras maneiras. Para obter mais informações, confira [Implantando aplicativos e serviços Web ASP.NET](/aspnet/overview/deployment).

- **Área de trabalho do Windows**: você pode publicar um aplicativo de área de trabalho do Windows em um servidor Web ou em um compartilhamento de arquivos de rede usando a implantação do ClickOnce. Os usuários podem, então, instalar o aplicativo com um único clique. Para obter mais informações, consulte os seguintes artigos:

  - [Implantar um aplicativo de área de trabalho do Windows .NET Framework usando o ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
  - [Implantar um aplicativo de área de trabalho do Windows .NET usando o ClickOnce](quickstart-deploy-using-clickonce-folder.md)
  - [Implantar um aplicativo C++/CLR usando o ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)

## <a name="publish-to-microsoft-store"></a>Publicar na Microsoft Store

No Visual Studio, você pode criar pacotes de aplicativos para implantação na Microsoft Store.

- **UWP**: você pode empacotar seu aplicativo e implantá-lo usando itens de menu. Para saber mais, confira [Empacotar um aplicativo UWP usando o Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Captura de tela que mostra a criação de um pacote de aplicativo.](../deployment/media/feature-tour-create-app-package.png)

- **Área de trabalho do Windows**: você pode implantar o no Microsoft Store usando a ponte de desktop a partir do Visual Studio 2017 versão 15,4. Para fazer isso, comece criando um Projeto de Empacotamento de Aplicativos do Windows. Para obter mais informações, confira [Empacotar um aplicativo da área de trabalho para a Microsoft Store (Ponte de Desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Captura de tela que mostra a seleção do projeto de empacotamento de aplicativos Windows.](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Implantar em um dispositivo (UWP)

Se você estiver implantando um aplicativo UWP para teste em um dispositivo, consulte [executar aplicativos UWP em um computador remoto no Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Criar um pacote de instalador (área de trabalho do Windows)

Se você precisar de uma instalação mais complexa de um aplicativo de área de trabalho do que o ClickOnce pode fornecer, poderá criar um pacote de Windows Installer (arquivo de instalação MSI ou EXE) ou um bootstrapper personalizado.

- Um pacote do instalador baseado em MSI pode ser criado usando a [extensão WiX do Visual Studio 2017 do conjunto de ferramentas](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension). Este é um conjunto de ferramentas de linha de comando.
- Um pacote do instalador MSI ou EXE pode ser criado usando o [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) do Flexera software. O InstallShield pode ser usado com o Visual Studio 2017 e versões posteriores. Não há suporte para a Community Edition.

  > [!NOTE]
  > O InstallShield Limited Edition não está mais incluído no Visual Studio e não tem suporte no Visual Studio 2017 e versões posteriores. Verifique com o [Flexera software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) sobre disponibilidade futura.

- Um pacote do instalador MSI ou EXE pode ser criado usando um projeto de instalação (vdproj). Para usar essa opção, instale a [extensão de Projetos de Instalador do Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).
- Você também pode instalar os componentes de pré-requisitos para aplicativos de área de trabalho configurando um instalador genérico, que é conhecido como bootstrapper. Para obter mais informações, consulte [pré-requisitos de implantação do aplicativo](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-a-test-lab"></a>Implantar em um laboratório de teste

Você pode permitir desenvolvimento e testes mais sofisticados implantando seus aplicativos em ambientes virtuais. Para obter mais informações, confira [Testar em um ambiente de laboratório](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Implantação contínua

Você pode usar Azure Pipelines para permitir a implantação contínua do seu aplicativo. Para obter mais informações, confira [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true) e [Implantar no Azure](/azure/devops/deploy-azure/index?view=vsts&preserve-view=true).

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
| **LightSwitch** | O LightSwitch não é mais compatível desde o Visual Studio 2017, mas ainda pode ser implantado no Visual Studio 2015 e anteriores. | [Implantando aplicativos do LightSwitch](/previous-versions/ff872288(v=vs.140)) |

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você obteve uma visão geral das opções de implantação para diferentes aplicativos.

> [!div class="nextstepaction"]
> [Quais opções de publicação são adequadas para mim?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)