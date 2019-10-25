---
title: Publicar no Serviço de Aplicativo do Azure
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 4bbff0c2d149afddc355afe5f6c93e9d0aea54c0
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806902"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publicar um aplicativo Web no Serviço de Aplicativo do Azure usando o Visual Studio

Para aplicativos ASP.NET, ASP.NET Core, Node.js e .NET Core, publique no Serviço de Aplicativo do Azure ou no Serviço de Aplicativo do Azure no Linux (usando contêineres) usando um dos métodos a seguir.

* Para implantação contínua (ou automática) de aplicativos, use o Azure DevOps com [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Para implantação única (ou manual) de aplicativos, use a ferramenta **Publicar** no Visual Studio para implantar aplicativos ASP.NET, ASP.NET Core, Node.js e .NET Core no Serviço de Aplicativo do Azure ou Serviço de Aplicativo para Linux (usando contêineres). Para aplicativos Python, siga as etapas em [Python – Publicar no Serviço de Aplicativo do Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

Este artigo descreve como usar a ferramenta **Publicar** para uma implantação única.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publicar no Serviço de Aplicativo do Azure

1. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e escolha **Publicar** (ou use o item de menu **Criar** > **Publicar**).

    ![O comando publicar no menu de contexto do projeto no Gerenciador de Soluções](../deployment/media/quickstart-publish.png "Escolha Publicar")

1. Se você já tiver configurado anteriormente quaisquer perfis de publicação, o painel **Publica** será exibido; nesse caso, selecione **Criar novo perfil**.

1. Na caixa de diálogo **Escolher um destino de publicação**, escolha **Serviço de Aplicativo**.

    ![Escolher serviço de Azure App](../deployment/media/quickstart-publish-azure.png "Escolher serviço de Azure App")

1. Selecione **Publicar**. A caixa de diálogo **Criar Serviço de Aplicativo** é exibida. Entre com sua conta do Azure, se necessário, e as configurações padrão do serviço de aplicativo populam os campos.

    ![Criar serviço de aplicativo](../deployment/media/quickstart-publish-settings-app-service.png "Criar Azure App serviço")

1. Selecione **Criar**. O Visual Studio implanta o aplicativo em seu Serviço de Aplicativo do Azure e o aplicativo Web é carregado em seu navegador. O painel **Publicar** das propriedades do projeto mostra a URL e outros detalhes do site.

    ![Publicar painel de propriedade mostrando um resumo do perfil](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Limpar recursos

Nas etapas anteriores, você criou recursos do Azure em um grupo de recursos. Se você espera não precisar desses recursos no futuro, pode excluí-los excluindo o grupo de recursos.
No menu esquerdo no portal do Azure, selecione **Grupo de recursos** e, em seguida, selecione **myResourceGroup**.
Na página do grupo de recursos, certifique-se de que os recursos listados são aqueles que você deseja excluir.
Selecione **Excluir**, digite **myResourceGroup** na caixa de texto e, em seguida, selecione **Excluir**.

## <a name="next-steps"></a>Próximas etapas

Neste início rápido, você aprendeu a usar o Visual Studio para criar um perfil de publicação para implantação no Azure. Também é possível configurar um perfil de publicação importando configurações de publicação do Serviço de Aplicativo do Azure.

> [!div class="nextstepaction"]
> [Importar configurações de publicação e implantar no Azure](tutorial-import-publish-settings-azure.md)
