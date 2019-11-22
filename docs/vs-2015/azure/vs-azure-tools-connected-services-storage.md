---
title: Adicionar o armazenamento do Azure usando serviços conectados
description: Adicionar Armazenamento do Azure ao seu aplicativo usando a caixa de diálogo Adicionar Serviços Conectados do Visual Studio
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 6d7bf7901ab33dc6dba50013ebdfa05c3188cd6c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300175"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Adicionando armazenamento do Azure usando os serviços conectados do Visual Studio
Com o Visual Studio, você pode conectar qualquer um dos seguintes Armazenamentos do Azure usando a caixa de diálogo **Adicionar Serviços Conectados**:

- Serviço de nuvem do C#
- Serviço móvel de back-end .NET
- Site ou serviço ASP.NET
- Principais serviços ASP.NET
- Serviço do Trabalho Web do Azure

A funcionalidade do serviço conectado adiciona todas as referências necessárias e o código de conexão ao seu projeto, bem como modifica os arquivos de configuração adequadamente.

Após a conclusão, a caixa de diálogo **Adicionar Serviços Conectados** exibe automaticamente a documentação detalhando as etapas necessárias para começar a trabalhar com armazenamento de blobs, filas e tabelas.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Conectar-se ao Armazenamento do Azure usando a caixa de diálogo Serviços Conectados
1. Abra o projeto no Visual Studio

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Serviços Conectados** e, no menu de contexto, selecione **Adicionar Serviço Conectado**.

    ![Adicionar serviço conectado do Azure](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. Na página **Serviços Conectados**, selecione **Armazenamento em Nuvem com o Armazenamento do Azure**.

    ![Adicionar Armazenamento do Azure](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. Na caixa de diálogo **Armazenamento do Azure**, selecione uma conta de armazenamento existente e escolha **Adicionar**.

    Se você precisar criar uma conta de armazenamento, passe para a próxima etapa. Caso contrário, pule para a etapa 6.

    ![Adicionar conta de armazenamento existente ao projeto](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Para criar uma conta de armazenamento:

   1. Selecione **Criar uma Nova Conta de Armazenamento** na parte inferior da caixa de diálogo.

   1. Preencha o diálogo **Criar Conta de Armazenamento** e selecione **Criar**.

       ![Nova conta de armazenamento do Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Quando a caixa de diálogo **Armazenamento do Azure** for exibida, a nova conta de armazenamento aparecerá na lista. Selecione a nova conta de armazenamento na lista e escolha **Adicionar**.

1. O serviço conectado de armazenamento aparece sob o nó **Referências de Serviço** do seu projeto.

## <a name="how-your-project-is-modified"></a>Como o projeto é modificado
Quando você acaba de fazer suas escolhas na caixa de diálogo, o Visual Studio adiciona referências e modifica determinados arquivos de configuração. As alterações específicas dependem do tipo de projeto:

- Projeto ASP.NET — [O que aconteceu — projetos ASP.NET](https://go.microsoft.com/fwlink/p/?LinkId=513126)
- Projeto de Núcleo ASP.NET — [O que aconteceu — projetos ASP.NET 5](https://go.microsoft.com/fwlink/p/?LinkId=513124)
- Projeto de serviço de nuvem (funções Web e funções de trabalho) — [O que aconteceu — projetos Serviço de Nuvem](https://go.microsoft.com/fwlink/p/?LinkId=516965)
- Projetos de Trabalho Web — [O que aconteceu — projetos de Trabalho Web](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Próximas etapas
- [Fórum do MSDN: armazenamento do Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Blog da equipe do Armazenamento do Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Documentação do Armazenamento do Azure](https://docs.microsoft.com/azure/storage/)
