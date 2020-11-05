---
title: Adicionar o Azure Signalr usando serviços conectados | Microsoft Docs
description: Adicionar o Azure Signalr ao seu aplicativo usando o Visual Studio para adicionar um serviço conectado
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 7c61d91ed3824d3ed9c33f579c321e471edb5a4e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398976"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Adicionar o Azure Signalr usando os serviços conectados do Visual Studio

Com o Visual Studio, você pode conectar qualquer um dos seguintes itens ao serviço de Signaler do Azure usando o recurso de **Serviços conectados** :

- .NET Framework aplicativo de console
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (incluindo aplicativo de console, WPF, Windows Forms, biblioteca de classes)
- Função de trabalho do .NET Core
- Azure Functions
- Plataforma Universal do Windows aplicativo
- Xamarin
- Cordova

A funcionalidade do serviço conectado adiciona todas as referências necessárias e o código de conexão ao seu projeto, bem como modifica os arquivos de configuração adequadamente.

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Serviços conectados no Visual Studio para Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Pré-requisitos

- Visual Studio com a carga de trabalho do Azure instalada.
- Um projeto de um dos tipos com suporte

## <a name="connect-to-azure-signalr-using-connected-services"></a>Conectar-se ao Azure Signalr usando serviços conectados

1. Abra o projeto no Visual Studio.

1. Em **Gerenciador de soluções** , clique com o botão direito do mouse no nó **Serviços conectados** e, no menu de contexto, selecione **Adicionar serviço conectado**.

1. Na guia **Serviços conectados** , selecione o ícone + para **dependências de serviço**.

    ![Adicionar dependência de serviço](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na página **Adicionar dependência** , selecione **serviço de signaler do Azure**.

    ![Adicionar serviço de Signaler do Azure](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Se você ainda não tiver entrado, entre em sua conta do Azure. Se você não tiver uma conta do Azure, poderá se inscrever para uma [avaliação gratuita](https://azure.microsoft.com/account/free).

1. Na tela **Configurar o signalr do Azure** , selecione um componente de Signaler do Azure existente e selecione **Avançar**.

    Se você precisar criar um novo componente, vá para a próxima etapa. Caso contrário, passe à etapa 7.

    ![Conectar-se a um componente de Signaler do Azure existente](./media/azure-signalr-add-connected-service/created-signalr.png)

1. Para criar uma instância do serviço de Signaler do Azure:

   1. Selecione **criar uma nova instância do serviço de signaler do Azure** na parte inferior da tela.

   1. Preencha o **serviço de signaler do Azure: criar nova** tela e selecione **criar**.

       ![Nova instância do serviço de Signaler do Azure](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. Quando a tela **configurar serviço de signaler do Azure** é exibida, a nova instância é exibida na lista. Selecione a nova instância na lista e selecione **Avançar**.

1. Insira um nome de cadeia de conexão ou escolha o padrão e escolha se deseja que a cadeia de conexão seja armazenada em um arquivo de segredos local ou em [Azure Key Vault](/azure/key-vault).

   ![Especificar cadeia de conexão](./media/azure-signalr-add-connected-service/connection-string.png)

1. A tela **Resumo das alterações** mostra todas as modificações que serão feitas ao seu projeto se você concluir o processo. Se as alterações parecerem OK, escolha **concluir**.

   ![Resumo das alterações](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. A conexão aparece na seção **dependências de serviço** da guia **Serviços conectados** .

   ![Dependências de serviço](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Confira também

- [Página do produto Signaler do Azure](https://azure.microsoft.com/services/signalr-service/)
- [Documentação do Serviço do Azure SignalR](/azure/azure-signalr)
- [Serviço conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)
