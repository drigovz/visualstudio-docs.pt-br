---
title: Publicar em um site
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
ms.openlocfilehash: 7ec5ea0b52c5d0708630a30b7d2b80be2275f3a9
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173665"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publique um aplicativo Web em um site usando o Visual Studio

É possível usar a ferramenta **Publicar** para publicar aplicativos ASP.NET, ASP.NET Core, .NET Core e Python em um site do Visual Studio. Para Node.js, há suporte para as etapas, mas a interface do usuário é diferente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Se você precisar publicar um aplicativo da área de trabalho do Windows em um compartilhamento de arquivo de rede, confira [Implantar um aplicativo da área de trabalho usando o ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# ou Visual Basic). Para C++/CLR, confira [Implantar um aplicativo nativo usando o ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou, para C/C++, confira [Implantar um aplicativo nativo usando um projeto de instalação](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publicar em um site

1. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e escolha **Publicar** (ou use o item de menu **Criar** > **Publicar**).

    ![O comando publicar no menu de contexto do projeto no Gerenciador de Soluções](../deployment/media/quickstart-publish.png "Escolha Publicar")

1. Se você já tiver configurado anteriormente quaisquer perfis de publicação, o painel **Publicar** será exibido. Selecione **Criar novo perfil**.

1. Na caixa de diálogo **publicar** , escolha **servidor Web (IIS)**.

    ![Escolher destino de publicação](../deployment/media/quickstart-publish-iis.png "Escolha IIS, FTP, etc.")

1. Escolha **implantação da Web** como o método de implantação. A Implantação da Web simplifica a implantação de aplicativos Web e sites para servidores do IIS e precisa ser instalada como um aplicativo no servidor. Use o [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx) para instalá-la.

    ![Escolher método de implantação](../deployment/media/quickstart-publish-iis-web-deploy.png "Escolha IIS, FTP, etc.")

1. Defina as configurações necessárias para o método de publicação e selecione **concluir**. 

    ![Detalhes da conexão do Implantação da Web](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Para publicar, selecione **publicar** na página Resumo. A janela de Saída mostra o progresso da implantação e os resultados.

## <a name="next-steps"></a>Próximas etapas

Neste início rápido, você aprendeu a usar o Visual Studio para criar um perfil de publicação. Também é possível configurar um perfil de publicação importando as configurações de publicação.

> [!div class="nextstepaction"]
> [Importar configurações de publicação e implantar no IIS](tutorial-import-publish-settings-iis.md)
