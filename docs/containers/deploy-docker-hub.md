---
title: Implantar um contêiner Docker ASP.NET core para o Docker Hub | Microsoft Docs
description: Saiba como usar o Visual Studio Container Tools para implantar um aplicativo web ASP.NET Core no Docker Hub
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: b033825bbe8facbeae3dcdee6a5b563461921522
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188752"
---
# <a name="deploy-to-docker-hub"></a>Implantar no Docker Hub

O Docker Hub fornece um serviço de hospedagem conveniente para seus repositórios de imagem. Você pode facilmente implantar no Docker Hub manualmente do Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Crie uma conta Docker e um repositório do Docker Hub

[Inscreva-se em](https://hub.docker.com/signup) uma conta Docker, se você ainda não tiver uma.

Se você não tiver um repositório do Docker Hub, crie um no [Docker Hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Publique a imagem de um único projeto para o Docker Hub

1. Clique com o botão direito do mouse no nó do projeto e escolha **Publicar...**. Uma tela mostrando opções de implantação é exibida.

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Em **Pick a publish target**, escolha Container **Registry**e escolha Docker **Hub**. A caixa de diálogo THe **Docker Hub** é exibida.

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Se você estiver se conectando ao seu próprio repositório (não faz parte de uma organização), deixe a caixa de seleção para **publicar em um repositório pessoal** verificado. Se o repositório for de propriedade de uma organização, limpe a caixa de seleção e digite o nome da organização. Digite seu nome de usuário e senha do Docker para sua conta Docker que tenha permissões para acessar o repositório ao que você está se conectando e, em seguida, **selecione Salvar**.  

   O Visual Studio tenta implantar sua imagem no Docker Hub.  Se for bem-sucedida, a tela **Publicar** será exibida com a URL para a imagem do repositório, a tag de imagem, o repositório e a configuração de compilação** (por exemplo, **Release**).

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Você pode atualizar a imagem a qualquer momento clicando no botão **Publicar** nesta página.  Ou, você pode modificar ou remover o perfil, usando os links abaixo da URL.

## <a name="next-steps"></a>Próximas etapas

Publique no [Registro de Contêineres do Azure](/azure/container-registry/) seguindo as etapas do [Deploy to Azure Container Registry](hosting-web-apps-in-docker.md).

Configure integração e entrega contínua (CI/CD) com [a Azure Pipelines](/azure/devops/pipelines/?view=azure-devops).

## <a name="see-also"></a>Confira também

[Implantar no Azure App Service](deploy-app-service.md)
[Visual Studio Container Tools](/visualstudio/containers/).