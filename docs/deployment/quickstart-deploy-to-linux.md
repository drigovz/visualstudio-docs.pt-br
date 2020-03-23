---
title: Publicar no Serviço de Aplicativo no Linux
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 1e05862aa57c24bfa8f17d551762054278dd6e52
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806866"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publicar um aplicativo ASP.NET Core no Serviço de Aplicativo no Linux usando o Visual Studio

Do Visual Studio 2017 versão 15.7 em diante, você pode publicar aplicativos ASP.NET Core para o Serviço de Aplicativo do Azure para Linux (usando contêineres) usando um dos métodos a seguir.

* Para implantação contínua (ou automática) de aplicativos, use o Azure DevOps com [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Para implantação única (ou manual) de aplicativos, use a ferramenta **Publicar** no Visual Studio para publicar aplicativos ASP.NET Core no Serviço de Aplicativo do Azure para Linux (usando contêineres).

Este artigo descreve como usar a ferramenta **Publicar** para uma implantação única.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publicar no Serviço de Aplicativo no Linux

1. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e escolha **Publicar** (ou use o item de menu **Criar** > **Publicar**).

    ![O comando Publicar no menu de contexto do projeto no Solution Explorer](../deployment/media/quickstart-publish.png "Escolha Publicar")

1. Se você já tiver configurado anteriormente quaisquer perfis de publicação, o painel **Publica** será exibido; nesse caso, selecione **Criar novo perfil**.

1. Na caixa de diálogo **Escolher um destino de publicação**, escolha **Serviço de Aplicativo no Linux**.

    ![Escolha o serviço de aplicativos do Azure](../deployment/media/quickstart-publish-linux.png "Escolha o serviço de aplicativos do Azure")

1. Selecione **Publicar**. A caixa de diálogo **Criar Serviço de Aplicativo** é exibida. Entre com sua conta do Azure, se necessário, e as configurações padrão do serviço de aplicativo populam os campos.

    ![Criar Serviço de Aplicativo](../deployment/media/quickstart-publish-settings-app-service-linux.png "Criar serviço de aplicativo do Azure")

1. Selecione **Criar**. O Visual Studio implanta o aplicativo em seu Serviço de Aplicativo do Azure e o aplicativo Web é carregado em seu navegador. O painel **Publicar** das propriedades do projeto mostra a URL e outros detalhes do site.

    ![Publicar painel de propriedade mostrando um resumo do perfil](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Limpar recursos

Nas etapas anteriores, você criou os recursos do Azure em um grupo de recursos. Se você não espera precisar desses recursos no futuro, poderá excluí-los ao excluir o grupo de recursos.
No menu à esquerda no portal do Azure, selecione **Grupos de recursos** e, em seguida, selecione **myResourceGroup**.
Na página do grupo de recursos, certifique-se de que os recursos listados são aqueles que deseja excluir.
Selecione **Excluir**, digite **myResourceGroup** na caixa de texto e selecione **Excluir**.

## <a name="next-steps"></a>Próximas etapas

Neste início rápido, você aprendeu a usar o Visual Studio para criar um perfil de publicação para implantação no Serviço de Aplicativo no Linux. Talvez você queira saber mais sobre como publicar no Linux usando o Azure.

> [!div class="nextstepaction"]
> [Serviço de Aplicativo do Linux](/azure/app-service/containers/app-service-linux-intro)
