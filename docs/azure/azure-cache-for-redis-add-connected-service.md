---
title: Adicionar o cache do Azure para Redis usando os serviços conectados | Microsoft Docs
description: Adicionar o cache do Azure para suporte do Redis ao seu aplicativo usando o Visual Studio para adicionar um serviço conectado
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: ad233d51e271dfbacb80b7f5f2792d546a8a3e0a
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903047"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Adicionar o cache do Azure para Redis usando os serviços conectados do Visual Studio

Com o Visual Studio, você pode conectar qualquer um dos seguintes itens ao cache do Azure para Redis usando o recurso de **Serviços conectados** :

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>Conectar-se ao cache do Azure para Redis usando os serviços conectados

1. Abra o projeto no Visual Studio.

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **Serviços conectados** e, no menu de contexto, selecione **Adicionar serviço conectado**.

1. Na guia **Serviços conectados** , selecione o ícone + para **dependências de serviço**.

    ![Adicionar dependência de serviço](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na página **Adicionar dependência** , selecione **cache do Azure para Redis**.

    ![Adicionar o Cache do Azure para Redis](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Se você ainda não tiver entrado, entre em sua conta do Azure. Se você não tiver uma conta do Azure, poderá se inscrever para uma [avaliação gratuita](https://azure.microsoft.com/account/free).

1. Na tela **Configurar o cache do Azure para Redis** , selecione um cache do Azure existente para Redis e selecione **Avançar**.

    Se você precisar criar um novo componente, vá para a próxima etapa. Caso contrário, passe à etapa 7.

    ![Conectar-se ao cache do Azure existente para Redis](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. Para criar um cache Redis do Azure:

   1. Selecione **criar um novo cache Redis do Azure** na parte inferior da tela.

   1. Preencha o **cache do Azure para Redis: criar nova** tela e selecione **criar**.

       ![Novo cache do Azure para Redis](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. Quando a tela **Configurar cache do Azure para Redis** for exibida, o novo cache aparecerá na lista. Selecione o novo banco de dados na lista e selecione **Avançar**.

1. Insira um nome de cadeia de conexão ou escolha o padrão e escolha se deseja que a cadeia de conexão seja armazenada em um arquivo de segredos local ou em [Azure Key Vault](/azure/key-vault).

   ![Especificar cadeia de conexão](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. A tela **Resumo das alterações** mostra todas as modificações que serão feitas ao seu projeto se você concluir o processo. Se as alterações parecerem OK, escolha **concluir**.

   ![Resumo das alterações](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. A conexão aparece na seção **dependências de serviço** da guia **Serviços conectados** .

   ![Dependências de serviço](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Confira também

- [Cache do Azure para a página do produto Redis](https://azure.microsoft.com/services/cache)
- [Documentação do cache do Azure para Redis](/azure/azure-cache-for-redis/)
- [Serviço conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)