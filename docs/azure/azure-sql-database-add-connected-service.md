---
title: Adicionar uma conexão ao banco de dados SQL do Azure | Microsoft Docs
description: Adicionar a conexão de banco de dados SQL do Azure ao seu aplicativo usando os serviços conectados do Visual Studio
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4d720c51d7245d60d40c286c71976132a119a56f
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902864"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Adicionar uma conexão ao banco de dados SQL do Azure

Com o Visual Studio, você pode conectar qualquer um dos seguintes itens ao banco de dados SQL do Azure usando o recurso **Serviços conectados** :

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

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Conectar-se ao banco de dados SQL do Azure usando serviços conectados

1. Abra o projeto no Visual Studio.

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **Serviços conectados** e, no menu de contexto, selecione **Adicionar serviço conectado**.

1. Na guia **Serviços conectados** , selecione o ícone + para **dependências de serviço**.

    ![Adicionar dependência de serviço](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na página **Adicionar dependência** , selecione **banco de dados SQL do Azure**.

    ![Adicionar serviço de banco de dados SQL do Azure](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Se você ainda não tiver entrado, entre em sua conta do Azure. Se você não tiver uma conta do Azure, poderá se inscrever para uma [avaliação gratuita](https://azure.microsoft.com/account/free).

1. Na tela **configurar banco de dados SQL do Azure** , selecione um banco de dados SQL do Azure existente e selecione **Avançar**.

    Se você precisar criar um novo componente, vá para a próxima etapa. Caso contrário, passe à etapa 7.

    ![Conectar-se ao componente existente do banco de dados SQL do Azure](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Para criar um banco de dados SQL do Azure:

   1. Selecione **criar um banco de dados SQL** na parte inferior da tela.

   1. Preencha o **banco de dados SQL do Azure: criar nova** tela e selecione **criar**.

       ![Novo banco de dados SQL do Azure](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Quando a tela **configurar banco de dados SQL do Azure** for exibida, o novo banco de dados aparecerá na lista. Selecione o novo banco de dados na lista e selecione **Avançar**.

1. Insira um nome de cadeia de conexão ou escolha o padrão e escolha se deseja que a cadeia de conexão seja armazenada em um arquivo de segredos local ou em [Azure Key Vault](/azure/key-vault).

   ![Especificar cadeia de conexão](./media/azure-sql-database-add-connected-service/connection-string.png)

1. A tela **Resumo das alterações** mostra todas as modificações que serão feitas ao seu projeto se você concluir o processo. Se as alterações parecerem OK, escolha **concluir**.

   ![Resumo das alterações](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Se for solicitado a definir regras de firewall, escolha **Sim**.

   ![Regras de firewall](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. A conexão aparece na seção **dependências de serviço** da guia **Serviços conectados** .

   ![Dependências de serviço](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Confira também

- [Página de produto do banco de dados SQL do Azure](https://azure.microsoft.com/services/sql-database/)
- [Documentação do Banco de Dados SQL do Azure](/azure/azure-sql/database/)
- [Serviço conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)
