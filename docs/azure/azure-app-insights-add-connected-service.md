---
title: Adicionar informações de Aplicativo Azure usando os serviços conectados | Microsoft Docs
description: Adicionar informações de Aplicativo Azure ao seu aplicativo usando o Visual Studio para adicionar um serviço conectado
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 5b93d5b15cbbd3ffcb1f8afb65afe6e1c2c371b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841218"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Adicionar informações de Aplicativo Azure usando os serviços conectados do Visual Studio

Com o Visual Studio, você pode conectar qualquer um dos seguintes para Aplicativo Azure insights usando o recurso de **Serviços conectados** :

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

## <a name="connect-to-azure-application-insights-using-connected-services"></a>Conectar-se a Aplicativo Azure insights usando serviços conectados

1. Abra o projeto no Visual Studio.

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **Serviços conectados** e, no menu de contexto, selecione **Adicionar serviço conectado**.

1. Na guia **Serviços conectados** , selecione o ícone + para **dependências de serviço**.

    ![Adicionar dependência de serviço](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na página **Adicionar dependência** , selecione **aplicativo Azure insights**.

    ![Adicionar informações de Aplicativo Azure](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    Se você ainda não tiver entrado, entre em sua conta do Azure. Se você não tiver uma conta do Azure, poderá se inscrever para uma [avaliação gratuita](https://azure.microsoft.com/account/free).

1. Na tela **configurar informações do aplicativo Azure** , selecione um componente existente do aplicativo Azure insights e selecione **Avançar**.

    Se você precisar criar um novo componente, vá para a próxima etapa. Caso contrário, passe à etapa 7.

    ![Conectar-se ao componente de Application Insights existente](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. Para criar um componente de Application Insights:

   1. Selecione **criar um novo componente Application insights** na parte inferior da tela.

   1. Preencha o **Application insights: criar nova** tela e selecione **criar**.

       ![Novo componente do insights Azure App](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. Quando a tela **Configurar insights aplicativo Azure** for exibida, o novo componente aparecerá na lista. Selecione o novo componente na lista e selecione **Avançar**.

1. Insira um nome de chave de instrumentação ou escolha o padrão e escolha se deseja que a cadeia de conexão seja armazenada em um arquivo de segredos local ou em [Azure Key Vault](/azure/key-vault).

   ![Especificar cadeia de conexão](./media/azure-app-insights-add-connected-service/connection-string.png)

1. A tela **Resumo das alterações** mostra todas as modificações que serão feitas ao seu projeto se você concluir o processo. Se as alterações parecerem OK, escolha **concluir**.

   ![Resumo das alterações](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. A conexão aparece na seção **dependências de serviço** da guia **Serviços conectados** .

   ![Dependências de serviço](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Confira também

- [Página do produto Azure Monitor](https://azure.microsoft.com/services/monitor/)
- [Documentação do insights do Azure App](/azure/azure-monitor/app/app-insights-overview/)
- [Serviço conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)
