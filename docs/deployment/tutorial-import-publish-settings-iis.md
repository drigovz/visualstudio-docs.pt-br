---
title: Publicar no IIS importando configurações de publicação
description: Criar e importar um perfil de publicação para implantar um aplicativo no IIS por meio do Visual Studio
ms.date: 01/31/2019
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e0c7309f52fbc8056f09e5a59afcfdefaa8d0bf
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680132"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publicar um aplicativo no IIS importando configurações de publicação no Visual Studio

É possível usar a ferramenta **Publicar** para importar configurações de publicação e, em seguida, implantar seu aplicativo. Neste artigo, usamos configurações de publicação para o IIS, mas é possível usar etapas semelhantes para importar configurações de publicação do [Serviço de Aplicativo do Azure](../deployment/tutorial-import-publish-settings-azure.md). Em alguns cenários, o uso de um perfil de configurações de publicação pode ser mais rápido do que configurar manualmente a implantação no IIS para cada instalação do Visual Studio.

Essas etapas se aplicam a aplicativos ASP.NET, ASP.NET Core e .NET Core no Visual Studio.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Configurar o IIS para poder gerar um arquivo de configurações de publicação
> * Criar um arquivo de configurações de publicação
> * Importar o arquivo de configurações de publicação para o Visual Studio
> * Implantar o aplicativo no IIS

Um arquivo de configurações de publicação (*\*.publishsettings*) é diferente de um perfil de publicação (*\*.pubxml*) criado no Visual Studio. Um arquivo de configurações de publicação é criado pelo IIS ou pelo Serviço de Aplicativo do Azure ou pode ser criado manualmente e, em seguida, pode ser importado para o Visual Studio.

> [!NOTE]
> Se você precisar copiar um perfil de publicação do Visual Studio (arquivo \*.pubxml) de uma instalação do Visual Studio para outra, será possível encontrar o perfil de publicação, *\<nomedoperfil\>.pubxml*, na pasta *\\<nomedoprojeto\>\Properties\PublishProfiles* para tipos de projeto gerenciados. Para sites, examine embaixo da pasta *\App_Data*. Os perfis de publicação são arquivos XML do MSBuild.

## <a name="prerequisites"></a>Pré-requisitos

::: moniker range=">=vs-2019"

* É necessário ter o Visual Studio 2019 instalado e a carga de trabalho de desenvolvimento do **ASP.NET e desenvolvimento Web**.

    Se você ainda não instalou o Visual Studio, acesse a página  [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalá-lo gratuitamente.
::: moniker-end

::: moniker range="vs-2017"

* É necessário ter o Visual Studio 2017 instalado e a carga de trabalho de desenvolvimento do **ASP.NET e desenvolvimento Web**.

    Se você ainda não instalou o Visual Studio, acesse a página  [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalá-lo gratuitamente.
::: moniker-end

* No servidor, você precisa estar executando o Windows Server 2012 ou 2016 e precisa ter a [função de servidor Web do IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) configurada corretamente (necessário para gerar o arquivo de configurações de publicação (*\*.publishsettings*)). O ASP.NET 4.5 ou o ASP.NET Core também precisam ser instalados no servidor. Para configurar o ASP.NET 4.5, confira [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Para configurar o ASP.NET Core, confira [Hospedar o ASP.NET Core no Windows com o IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Criar um novo projeto ASP.NET no Visual Studio

1. No computador que executa o Visual Studio, crie um projeto.

    Escolha o modelo correto. Neste exemplo, escolha **Aplicativo Web ASP.NET (.NET Framework)** ou (apenas para C#) **Aplicativo Web ASP.NET Core** e, em seguida, clique em **OK**.

    Se os modelos de projeto especificados não forem exibidos, clique no link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**. O Instalador do Visual Studio é iniciado. Instale a carga de trabalho de **ASP.NET e desenvolvimento Web**.

    O modelo de projeto que você escolher (ASP.NET ou ASP.NET Core) precisa corresponder à versão do ASP.NET instalada no servidor Web.

1. Escolha **MVC** (.NET Framework) ou **Aplicativo Web (Model-View-Controller)** (para .NET Core) e certifique-se de que **Sem autenticação** esteja selecionado. Em seguida, clique em **OK**.

1. Digite um nome como **MyWebApp** e clique em **OK**.

    O Visual Studio cria o projeto.

1. Escolha **Criar** > **Criar solução** para criar o projeto.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalar e configurar a Implantação da Web no Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Criar o arquivo de configurações de publicação no IIS no Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar as configurações de publicação no Visual Studio e implantar

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Depois que o aplicativo for implantado com êxito, ele deverá ser iniciado automaticamente. Se ele não for iniciado do Visual Studio, inicie o aplicativo no IIS. Para ASP.NET Core, é necessário certificar-se de que o campo do pool de aplicativos para o **DefaultAppPool** está definido como **Sem código gerenciado**.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou um arquivo de configurações de publicação, importou-o para o Visual Studio e implantou um aplicativo ASP.NET no IIS. Talvez você queira ter uma visão geral de outras opções de publicação no Visual Studio.

> [!div class="nextstepaction"]
> [Introdução à implantação](../deployment/deploying-applications-services-and-components.md)
