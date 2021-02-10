---
title: Publicar no Azure com a importação de configurações de publicação
description: Criar e importar um perfil de publicação para implantar um aplicativo por meio do Visual Studio no Serviço de Aplicativo do Azure
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50a65d681693bd9c1421767d2cac47f65b685e6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945039"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publicar um aplicativo no Serviço de Aplicativo do Azure com a importação de configurações de publicação no Visual Studio

É possível usar a ferramenta **Publicar** para importar configurações de publicação e, em seguida, implantar seu aplicativo. Neste artigo, usamos configurações de publicação para o Serviço de Aplicativo do Azure, mas é possível usar etapas semelhantes para importar configurações de publicação do [IIS](../deployment/tutorial-import-publish-settings-iis.md). Em alguns cenários, o uso de um perfil de configurações de publicação pode ser mais rápido do que configurar manualmente a implantação no serviço para cada instalação do Visual Studio.

Essas etapas se aplicam a aplicativos ASP.NET, ASP.NET Core e .NET Core no Visual Studio. Também é possível importar as configurações de publicação de aplicativos [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

Neste tutorial, você irá:

> [!div class="checklist"]
> * Gerar um arquivo de configurações de publicação do Serviço de Aplicativo do Azure
> * Importar o arquivo de configurações de publicação para o Visual Studio
> * Implantar o aplicativo no Serviço de Aplicativo do Azure

Um arquivo de configurações de publicação (*\* . publishsettings*) é diferente de um perfil de publicação (*\* . Pubxml*) criado no Visual Studio. Um arquivo de configurações de publicação é criado pelo Serviço de Aplicativo do Azure e, em seguida, pode ser importado para o Visual Studio.

> [!NOTE]
> Se você só precisar copiar um perfil de publicação do Visual Studio (arquivo *\* . pubxml* ) de uma instalação do Visual Studio para outra, poderá encontrar o perfil de publicação, *\<profilename\> . pubxml*, na pasta *\\<ProjectName \> \Properties\PublishProfiles* para tipos de projeto gerenciado. Para sites, examine embaixo da pasta *\App_Data*. Os perfis de publicação são arquivos XML do MSBuild.

## <a name="prerequisites"></a>Pré-requisitos

::: moniker range=">=vs-2019"

* É necessário ter o Visual Studio 2019 instalado e a carga de trabalho de desenvolvimento do **ASP.NET e desenvolvimento Web**.

    Se você ainda não instalou o Visual Studio, vá para a página de [downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/) para instalá-lo gratuitamente.
::: moniker-end

::: moniker range="vs-2017"

* É necessário ter o Visual Studio 2017 instalado e a carga de trabalho de desenvolvimento do **ASP.NET e desenvolvimento Web**.

    Se você ainda não instalou o Visual Studio, vá para a página de [downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/) para instalá-lo gratuitamente.
::: moniker-end

* Crie um Serviço de Aplicativo do Azure. Para obter instruções detalhadas, confira [Implantar um aplicativo Web do ASP.NET Core no Azure usando o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Criar um novo projeto ASP.NET no Visual Studio

1. No computador que executa o Visual Studio, crie um projeto.

    Escolha o modelo correto. Neste exemplo, escolha **aplicativo web ASP.net (.NET Framework)** ou (somente para C#) **ASP.NET Core aplicativo Web** e, em seguida, selecione **OK**.

    Se você não vir os modelos de projeto especificados, vá para o link **abrir instalador do Visual Studio** no painel esquerdo da caixa de diálogo **novo projeto** . O Instalador do Visual Studio é iniciado. Instale o ASP.NET e a carga de trabalho de **desenvolvimento na Web** .

    O modelo de projeto que você escolher (ASP.NET ou ASP.NET Core) precisa corresponder à versão do ASP.NET instalada no servidor Web.

1. Escolha **MVC** (.NET Framework) ou **aplicativo Web (Model-View-Controller)** (para .NET Core) e verifique se **nenhuma autenticação** está selecionada e, em seguida, selecione **OK**.

1. Digite um nome como **myWebApp** e selecione **OK**.

    O Visual Studio cria o projeto.

1. Escolha **Compilar** compilar  >  **solução** para compilar o projeto.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Criar um arquivo de configurações de publicação no Serviço de Aplicativo do Azure

1. No portal do Azure, abra o Serviço de Aplicativo do Azure.

1. Vá para **obter perfil de publicação** e salve o perfil localmente.

    ![Obter o perfil de publicação](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Um arquivo com uma extensão *.publishsettings* foi gerado na localização em que ele foi salvo. O código a seguir mostra um exemplo parcial do arquivo (em uma formatação mais legível).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```

    Normalmente, o arquivo *.publishsettings anterior contém dois perfis de publicação que você pode usar no Visual Studio, uma para implantar usando a Implantação da Web e outro para implantar usando o FTP. O código anterior mostra o perfil de Implantação da Web. Os dois perfis serão importados posteriormente quando você importar o perfil.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar as configurações de publicação no Visual Studio e implantar

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou um arquivo de configurações de publicação, importou-o para o Visual Studio e implantou um aplicativo ASP.NET no Serviço de Aplicativo do Azure. Talvez você queira ter uma visão geral das opções de publicação no Visual Studio.

> [!div class="nextstepaction"]
> [Introdução à implantação](../deployment/deploying-applications-services-and-components.md)
