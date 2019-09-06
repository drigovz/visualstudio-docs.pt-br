---
title: Implantar um contêiner do Docker ASP.NET Core no serviço Azure App | Microsoft Docs
description: Saiba como usar as ferramentas de contêiner do Visual Studio para implantar um aplicativo Web ASP.NET Core no serviço Azure App
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 03/08/2019
ms.author: ghogen
ms.openlocfilehash: 9431046c57851e31a3711b4785f9cce45acab45f
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70312266"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Implantar um contêiner de ASP.NET Core no serviço Azure App usando o Visual Studio

Este tutorial orienta você pelo uso do Visual Studio para publicar seu aplicativo Web em contêineres ASP.NET Core em um [serviço Azure app](/azure/app-service). Azure App serviço é um serviço apropriado para um aplicativo Web de contêiner único hospedado no Azure.

Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) antes de começar.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial:

::: moniker range="vs-2017"
- Instale a última versão do [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) com a carga de trabalho "ASP.NET e desenvolvimento para a Web"
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) com a ASP.net e a carga de trabalho de *desenvolvimento da Web* .
::: moniker-end
- Instalar o [Docker desktop](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Criar um aplicativo Web ASP.NET Core

As etapas a seguir guiam você na criação de um aplicativo básico ASP.NET Core que será usado neste tutorial.

::: moniker range="vs-2017"
1. No menu do Visual Studio, selecione **Arquivo > Novo > Projeto**.
2. Na seção **Modelos** da caixa de diálogo **Novo Projeto**, selecione **Visual C# > Web**.
3. Selecione **Aplicativo Web ASP.NET Core**.
4. Dê um nome ao novo aplicativo (ou use o padrão) e selecione **OK**.
5. Selecione **Aplicativo Web**.
6. Verifique a caixa de seleção **Habilitar o suporte do Docker**.
7. Selecione o tipo de contêiner do **Linux** e clique em **OK**. Não há suporte para a implantação de contêineres do Windows no serviço Azure App como um contêiner.
::: moniker-end
::: moniker range=">= vs-2019"
1. Da janela de início do Visual Studio escolha **Criar um projeto**.
1. Escolha **Aplicativo Web ASP.NET Core** e escolha **Avançar**.
1. Dê um nome ao novo aplicativo (ou use o padrão) e escolha **Criar**.
1. Escolha **Aplicativo Web**.
1. Escolha se deseja ou não suporte a SSL usando a caixa de seleção **Configurar para HTTPS**.
1. Verifique a caixa de seleção **Habilitar o suporte do Docker**.
1. Selecione o tipo de contêiner do **Linux** e clique em **criar**. Não há suporte para a implantação de contêineres do Windows no serviço Azure App como um contêiner.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Implantar o contêiner no Azure

1. Clique com o botão direito no projeto em **Gerenciador de Soluções** e escolha **Publicar**.
1. Na caixa de diálogo Publicar destino, escolha **serviço de aplicativo Linux**.
1. Você pode publicar somente no serviço de aplicativo ou pode publicar no serviço de aplicativo e no ACR (registro de contêiner do Azure). Para publicar o contêiner em um ACR (registro de contêiner do Azure), escolha **criar novo serviço de aplicativo para contêineres**e clique em **publicar**.

   ![Captura de tela da caixa de diálogo publicar](media/deploy-app-service/publish-app-service-linux.PNG)

   Para publicar somente em um serviço de Azure App sem usar o registro de contêiner do Azure, escolha **criar novo**e clique em **publicar**.

1. Verifique se você está conectado com a conta que está associada à sua assinatura do Azure e escolha um nome exclusivo, uma assinatura, um grupo de recursos, um plano de hospedagem e um registro de contêiner (se aplicável) ou aceite os padrões.

   ![Captura de tela das configurações de publicação](media/deploy-app-service/publish-app-service-linux2.png)

1. Escolha **criar**. O contêiner é implantado no Azure no grupo de recursos e no registro de contêiner que você selecionou. Esse processo leva um pouco de tempo. Quando ela for concluída, a guia **publicar** mostrará informações sobre o que foi publicado, incluindo a URL do site.

   ![Captura de tela da guia publicar](media/deploy-app-service/publish-succeeded.PNG)

1. Clique no link do site para verificar se seu aplicativo funciona conforme o esperado no Azure.

   ![Captura de tela do aplicativo Web](media/deploy-app-service/web-application-running.png)

1. O perfil de publicação é salvo com todos os detalhes selecionados, como o grupo de recursos e o registro de contêiner.
1. Para implantar novamente com o mesmo perfil de publicação, use o botão **publicar** , o botão **publicar** na janela atividade de **publicação na Web** ou clique com o botão direito do mouse no projeto no **Gerenciador de soluções** e escolha o item **publicar** no menu de contexto.

## <a name="clean-up-resources"></a>Limpar recursos

Para remover todos os recursos do Azure associados a este tutorial, exclua o grupo de recursos usando o [portal do Azure](https://portal.azure.com). Para localizar o grupo de recursos associado a um aplicativo Web publicado, escolha **Exibir** > **outra** > **atividade de publicação na Web**do Windows e, em seguida, escolha o ícone de engrenagem. A guia **publicar** é aberta, que contém o grupo de recursos.

No portal do Azure, escolha **grupos de recursos**, selecione o grupo de recursos para abrir sua página de detalhes. Verifique se esse é o grupo de recursos correto e escolha **remover grupo de recursos**, digite o nome e escolha **excluir**.

## <a name="next-steps"></a>Próximas etapas

Configure a integração e a entrega contínuas (CI/CD) com [Azure pipelines](/azure/devops/pipelines/?view=azure-devops).

## <a name="see-also"></a>Consulte também

[Implantar no registro de contêiner do Azure](vs-azure-tools-docker-hosting-web-apps-in-docker.md)