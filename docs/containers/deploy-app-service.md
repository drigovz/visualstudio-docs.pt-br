---
title: Implantar um contêiner Docker ASP.NET para o serviço de aplicativos do Azure | Microsoft Docs
description: Saiba como usar o Visual Studio Container Tools para implantar um aplicativo web ASP.NET Core no Azure App Service
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 6c1d56f788294826853ad441313597255308bb39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027287"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Implantar um contêiner ASP.NET Core para o Azure App Service usando o Visual Studio

Este tutorial orienta você a usar o Visual Studio para publicar seu aplicativo web ASP.NET Core contêiner para um [Serviço de Aplicativos Azure](/azure/app-service). O Azure App Service é um serviço apropriado para um aplicativo web de contêiner único hospedado no Azure.

Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) antes de começar.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial:

::: moniker range="vs-2017"
- Instale a última versão do [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) com a carga de trabalho "ASP.NET e desenvolvimento para a Web"
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) com a carga de trabalho de *desenvolvimento Web e do ASP.NET*.
::: moniker-end
- Instale [o Docker Desktop](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Criar um aplicativo Web ASP.NET Core

As etapas a seguir guiam você na criação de um aplicativo básico ASP.NET Core que será usado neste tutorial.

::: moniker range="vs-2017"
1. No menu do Visual Studio, selecione **Arquivo > Novo > Projeto**.
2. Na seção **Modelos** da caixa de diálogo **Novo Projeto**, selecione **Visual C# > Web**.
3. Selecione **Aplicativo Web ASP.NET Core**.
4. Dê um nome ao novo aplicativo (ou use o padrão) e selecione **OK**.
5. Selecione **o Aplicativo web**.
6. Verifique a caixa de seleção **Habilitar o suporte do Docker**.
7. Selecione o tipo de contêiner **Linux** e clique em **OK**. Os contêineres do Windows não são suportados para implantar o Azure App Service como um contêiner.
::: moniker-end
::: moniker range=">= vs-2019"
1. Da janela de início do Visual Studio escolha **Criar um projeto**.
1. Escolha **Aplicativo Web ASP.NET Core** e escolha **Avançar**.
1. Dê um nome ao novo aplicativo (ou use o padrão) e escolha **Criar**.
1. Escolha **Aplicativo Web**.
1. Escolha se deseja ou não suporte a SSL usando a caixa de seleção **Configurar para HTTPS**.
1. Verifique a caixa de seleção **Habilitar o suporte do Docker**.
1. Selecione o tipo de contêiner e clique **em Criar**. Os contêineres do Windows não são suportados para implantar o Azure App Service como um contêiner.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Implantar o contêiner no Azure

1. Clique com o botão direito no projeto em **Gerenciador de Soluções** e escolha **Publicar**.
1. Na caixa de diálogo de destino publicar, escolha **O Serviço de Aplicativo Linux** ou Serviço de **Aplicativo**. Este é o sistema operacional que hospedará o servidor web.
1. Você pode publicar apenas no App Service, ou pode publicar tanto no App Service quanto no Acr (ACR). Para publicar o contêiner em um ACR (ACR) do Azure Container Registry (ACR), escolha **Criar um novo serviço de aplicativo para contêineres**e clique em **Publicar**.

   ![Captura de tela de publicar diálogo](media/deploy-app-service/publish-app-service-linux.PNG)

   Para publicar apenas em um serviço de aplicativo do Azure sem usar o Registro de Contêineres do Azure, escolha **Criar novo**e clique **em Publicar**.

1. Verifique se você está conectado com a conta associada à sua assinatura do Azure e escolha um nome exclusivo, assinatura, grupo de recursos, plano de hospedagem e registro de contêineres (se aplicável) ou aceite os padrões.

   ![Captura de tela das configurações de publicação](media/deploy-app-service/publish-app-service-linux2.png)

1. Escolha **Criar**. Seu contêiner é implantado no Azure no grupo de recursos e no registro de contêineres selecionados. Esse processo leva um pouco de tempo. Quando estiver concluído, a guia **Publicar** mostra informações sobre o que foi publicado, incluindo a URL do site.

   ![Captura de tela da guia publicar](media/deploy-app-service/publish-succeeded.PNG)

1. Clique no link do site para verificar se seu aplicativo funciona como esperado no Azure.

   ![Captura de tela do aplicativo web](media/deploy-app-service/web-application-running.png)

1. O perfil de publicação é salvo com todos os detalhes selecionados, como o grupo de recursos e o registro de contêineres.

1. Para implantar novamente com o mesmo perfil de publicação, use o botão **Publicar,** o botão **Publicar** na janela **Atividade de publicação da Web** ou clicar com o botão direito do mouse no projeto no Solution **Explorer** e escolha o item **Publicar** no menu de contexto.

## <a name="view-container-settings"></a>Exibir configurações do contêiner

No [portal Azure,](https://portal.azure.com)você pode abrir seu Serviço de Aplicativo implantado.

Você pode visualizar as configurações do serviço de aplicativo implantado abrindo o menu*de configurações* * Contêiner (quando estiver usando o Visual Studio 2019 versão 16.4 ou posterior).

![Captura de tela do menu Configurações de contêiner no portal Azure](media/deploy-app-service/container-settings-menu.png)

A partir daí, você pode visualizar as informações do contêiner, visualizar ou baixar logs ou configurar a implantação contínua. Consulte [o Azure App Service Continuous Deployment CI/CD](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Limpar recursos

Para remover todos os recursos do Azure associados a este tutorial, exclua o grupo de recursos usando o [portal Azure](https://portal.azure.com). Para encontrar o grupo de recursos associado a um aplicativo web publicado, escolha **Exibir** > **Outra atividade** > de publicação da**Web do**Windows e escolha o ícone de engrenagem. A **guia Publicar** é aberta, que contém o grupo de recursos.

No portal Azure, escolha **grupos de recursos,** selecione o grupo de recursos para abrir sua página de detalhes. Verifique se este é o grupo de recursos correto e, em seguida, escolha **Remover grupo de recursos,** digite o nome e escolha **Excluir**.

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre [o Azure App Service Linux](/azure/app-service/containers/app-service-linux-intro).

## <a name="see-also"></a>Confira também

[Implantar no Registro de Contêiner do Azure](hosting-web-apps-in-docker.md)