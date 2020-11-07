---
title: Publicar em um site
description: Saiba como usar a ferramenta de publicação para publicar aplicativos ASP.NET, ASP.NET Core, .NET Core e Python em um site do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 027350b6a51cae5e7be88643624adc6955de91e4
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350693"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publique um aplicativo Web em um site usando o Visual Studio

É possível usar a ferramenta **Publicar** para publicar aplicativos ASP.NET, ASP.NET Core, .NET Core e Python em um site do Visual Studio. Para Node.js, há suporte para as etapas, mas a interface do usuário é diferente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Se você precisar publicar um aplicativo da área de trabalho do Windows em um compartilhamento de arquivo de rede, confira [Implantar um aplicativo da área de trabalho usando o ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# ou Visual Basic). Para C++/CLR, confira [Implantar um aplicativo nativo usando o ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou, para C/C++, confira [Implantar um aplicativo nativo usando um projeto de instalação](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publicar em um site

1. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e escolha **Publicar** (ou use o item de menu **Criar** > **Publicar** ).

    ![O comando publicar no menu de contexto do projeto no Gerenciador de Soluções](../deployment/media/quickstart-publish.png "Escolha Publicar")

1. Se você já tiver configurado anteriormente quaisquer perfis de publicação, o painel **Publicar** será exibido. Selecione **Novo**.

1. Na janela **publicar** , escolha **servidor Web (IIS)**.

    ![Escolher destino de publicação](../deployment/media/quickstart-publish-iis.png "Escolha IIS, FTP, etc.")

1. Escolha **implantação da Web** como o método de implantação. A Implantação da Web simplifica a implantação de aplicativos Web e sites para servidores do IIS e precisa ser instalada como um aplicativo no servidor. Use o [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx) para instalá-la.

    ![Escolher método de implantação](../deployment/media/quickstart-publish-iis-web-deploy.png "Escolha IIS, FTP, etc.")

1. Defina as configurações necessárias para o método de publicação e selecione **concluir**. 

    ![Detalhes da conexão do Implantação da Web](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Para publicar, selecione **publicar** na página Resumo. A janela de Saída mostra o progresso da implantação e os resultados.

   Se precisar de ajuda para solucionar problemas ASP.NET Core no IIS, consulte [solucionar problemas ASP.NET Core no serviço Azure app e no IIS](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="next-steps"></a>Próximas etapas

Neste início rápido, você aprendeu a usar o Visual Studio para criar um perfil de publicação. Também é possível configurar um perfil de publicação importando as configurações de publicação.

> [!div class="nextstepaction"]
> [Importar configurações de publicação e implantar no IIS](tutorial-import-publish-settings-iis.md)
