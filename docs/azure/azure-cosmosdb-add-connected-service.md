---
title: Adicionar CosmosDB do Azure usando serviços conectados | Microsoft Docs
description: Adicionar suporte do Azure CosmosDB ao seu aplicativo usando o Visual Studio para adicionar um serviço conectado
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 2d23081f541fbc12581450c60c6eb4b09f20c64a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643359"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Adicionar Azure Cosmos DB ao seu aplicativo usando os serviços conectados do Visual Studio

Com o Visual Studio, você pode conectar qualquer um dos seguintes a Azure Cosmos DB usando o recurso **Serviços conectados** :

- .NET Framework aplicativo de console
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (incluindo aplicativo de console, WPF, Windows Forms, biblioteca de classes)
- Função de trabalho do .NET Core
- Funções do Azure
- Plataforma Universal do Windows aplicativo
- Xamarin
- Cordova

A funcionalidade do serviço conectado adiciona todas as referências necessárias e o código de conexão ao seu projeto, bem como modifica os arquivos de configuração adequadamente.

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Serviços conectados no Visual Studio para Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Pré-requisitos

- Visual Studio com a carga de trabalho do Azure instalada.
- Um projeto de um dos tipos com suporte

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>Conectar-se a Azure Cosmos DB usando os serviços conectados

1. Abra o projeto no Visual Studio.

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **Serviços conectados** e, no menu de contexto, selecione **Adicionar serviço conectado**.

1. Na guia **Serviços conectados** , selecione o ícone + para **dependências de serviço**.

    ![Adicionar dependência de serviço](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na página **Adicionar dependência** , selecione **Azure Cosmos DB**.

    ![Adicionar Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Se você ainda não tiver entrado, entre em sua conta do Azure. Se você não tiver uma conta do Azure, poderá se inscrever para uma [avaliação gratuita](https://azure.microsoft.com/account/free).

1. Na tela **Azure Cosmos DB** , selecione um Azure Cosmos DB existente e selecione **Avançar**.

    Se você precisar criar um banco de dados, vá para a próxima etapa. Caso contrário, passe à etapa 7.

    ![Adicionar Cosmos DB existente ao projeto](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Para criar um Azure Cosmos DB:

   1. Selecione **criar um novo Azure Cosmos DB** na parte inferior da tela.

   1. Preencha o **Azure Cosmos DB: criar nova** tela e selecione **criar**.

       ![Novo Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. Quando a caixa de diálogo **configurar Azure Cosmos DB** for exibida, o novo banco de dados aparecerá na lista. Selecione o novo banco de dados na lista e selecione **Avançar**.

1. Insira um nome de cadeia de conexão e escolha se deseja que a cadeia de conexão seja armazenada em um arquivo de segredos local ou em [Azure Key Vault](/azure/key-vault).

   ![Especificar cadeia de conexão](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. A tela **Resumo das alterações** mostra todas as modificações que serão feitas ao seu projeto se você concluir o processo. Se as alterações parecerem OK, escolha **concluir**.

   ![Resumo das alterações](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. A conexão aparece na seção **dependências de serviço** da guia **Serviços conectados** .

   ![Dependências de serviço](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Confira também

- [Página do produto Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)
- [Documentação do Azure Cosmos DB](/azure/cosmos-db/)
- [Serviço conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)
