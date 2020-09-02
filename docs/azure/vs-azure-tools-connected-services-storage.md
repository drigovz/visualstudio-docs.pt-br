---
title: Adicionar o Armazenamento do Azure usando serviços conectados | Microsoft Docs
description: Adicionar uma dependência do serviço de armazenamento do Azure ao seu aplicativo usando os serviços conectados do Visual Studio
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: f2f55a149420205435d9f64ea1f66c8c6854ec38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800509"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Adicionando armazenamento do Azure usando os serviços conectados do Visual Studio

Com o Visual Studio, você pode conectar qualquer um dos seguintes itens ao armazenamento do Azure usando o recurso **Serviços conectados** :

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

## <a name="connect-to-azure-storage-using-connected-services"></a>Conectar-se ao armazenamento do Azure usando serviços conectados

::: moniker range="vs-2017"

1. Abra o projeto no Visual Studio.

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **Serviços conectados** e, no menu de contexto, selecione **Adicionar serviço conectado**.

    ![Adicionar serviço conectado do Azure](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. Na página **Serviços Conectados**, selecione **Armazenamento em Nuvem com o Armazenamento do Azure**.

    ![Adicionar Armazenamento do Azure](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. Na caixa de diálogo **Armazenamento do Azure**, selecione uma conta de armazenamento existente e escolha **Adicionar**.

    Se você precisar criar uma conta de armazenamento, passe para a próxima etapa. Caso contrário, ignore a etapa 6.

    ![Adicionar conta de armazenamento existente ao projeto](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Para criar uma conta de armazenamento:

   1. Selecione **Criar uma Nova Conta de Armazenamento** na parte inferior da caixa de diálogo.

   1. Preencha o diálogo **Criar Conta de Armazenamento** e selecione **Criar**.

       ![Nova conta de armazenamento do Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Quando a caixa de diálogo **Armazenamento do Azure** for exibida, a nova conta de armazenamento aparecerá na lista. Selecione a nova conta de armazenamento na lista e escolha **Adicionar**.

1. O serviço conectado de armazenamento aparece sob o nó **Referências de Serviço** do seu projeto.
:::moniker-end

:::moniker range=">=vs-2019"

1. Abra o projeto no Visual Studio.

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **Serviços conectados** e, no menu de contexto, selecione **Adicionar serviço conectado**.

    ![Adicionar serviço conectado do Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Na guia **Serviços conectados** , selecione o ícone + para **dependências de serviço**.

    ![Adicionar dependência de serviço](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na página **Adicionar dependência** , selecione **armazenamento do Azure**.

    ![Adicionar Armazenamento do Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Se você ainda não tiver entrado, entre em sua conta do Azure. Se você não tiver uma conta do Azure, poderá se inscrever para uma [avaliação gratuita](https://azure.microsoft.com/account/free).

1. Na tela **Configurar armazenamento do Azure** , selecione uma conta de armazenamento existente e selecione **Avançar**.

    Se você precisar criar uma conta de armazenamento, passe para a próxima etapa. Caso contrário, ignore a etapa 6.

    ![Adicionar conta de armazenamento existente ao projeto](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. Para criar uma conta de armazenamento:

   1. Selecione **criar uma conta de armazenamento** na parte inferior da caixa de diálogo.

   1. Preencha o **armazenamento do Azure: criar nova** caixa de diálogo e selecione **criar**.

       ![Nova conta de armazenamento do Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. Quando a caixa de diálogo **Armazenamento do Azure** for exibida, a nova conta de armazenamento aparecerá na lista. Selecione a nova conta de armazenamento na lista e selecione **Avançar**.

1. Insira um nome de cadeia de conexão e escolha se deseja que a cadeia de conexão seja armazenada em um arquivo de segredos local ou em [Azure Key Vault](/azure/key-vault).

   ![Especificar cadeia de conexão](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. A tela **Resumo das alterações** mostra todas as modificações que serão feitas ao seu projeto se você concluir o processo. Se as alterações parecerem OK, escolha **concluir**.

   ![Resumo das alterações](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. O serviço conectado de armazenamento aparece sob o nó **Referências de Serviço** do seu projeto.
:::moniker-end

## <a name="see-also"></a>Confira também

- [Fórum do Armazenamento do Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Documentação do Armazenamento do Azure](/azure/storage/)
- [Serviço conectados (Visual Studio para Mac)](/visualstudio/mac/connected-services)
