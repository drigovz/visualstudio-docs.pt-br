---
title: Adicionar novas conexões
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 73b09384bd57fd4ea0890d107ce641e4b615559f
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154212"
---
# <a name="add-new-connections"></a>Adicionar novas conexões

Você pode testar sua conexão a um banco de dados ou serviço e explorar o conteúdo do banco de dados e esquemas, usando **Gerenciador de servidores**, **Cloud Explorer**, ou **Pesquisador de objetos do SQL Server**. A funcionalidade dessas janelas se sobrepõe até certo ponto. As diferenças básicas são:

- conexões de servidor

   Instalado por padrão no Visual Studio. Pode ser usado para testar as conexões e exibir bancos de dados do SQL Server, outros bancos de dados que têm um provedor ADO.NET instalados e alguns serviços do Azure. Também mostra objetos de baixo nível, como contadores de desempenho do sistema, logs de eventos e filas de mensagens. Se uma fonte de dados não tem nenhum provedor do ADO.NET, ele não aparecerá aqui, mas você pode ainda usá-lo do Visual Studio conectando-se por meio de programação.

- Cloud Explorer

   Instale essa janela manualmente como uma extensão do Visual Studio, selecionando **ferramentas** > **extensões e atualizações** > **Online**  >  **Visual Studio Marketplace**. Fornece funcionalidades especializadas para explorar e conectar-se aos serviços do Azure.

- Pesquisador de Objetos do SQL Server

   Instalado com o SQL Server Data Tools e visível sob o **exibição** menu. Se você não vi-lo existe, vá para **programas e recursos** no painel de controle, encontrar o Visual Studio e, em seguida, selecione **alteração** para executar novamente o instalador depois de selecionar a caixa de seleção para o SQL Server Data Tools. Use **Pesquisador de objetos do SQL Server** exibir bancos de dados SQL (se eles têm um provedor ADO.NET), criar novos bancos de dados, modificar esquemas, procedimentos armazenados de criar, recuperar cadeias de caracteres de conexão, exibir os dados e muito mais. Bancos de dados SQL que não tem nenhum provedor ADO.NET instalado não será mostrada aqui, mas você ainda pode se conectar a eles por meio de programação.

## <a name="add-a-connection-in-server-explorer"></a>Adicionar uma conexão no Gerenciador de servidores

Para criar uma conexão ao banco de dados, clique o **Adicionar Conexão** ícone na **Gerenciador de servidores**, ou clique com botão direito no **Gerenciador de servidores** no **dados Conexões** nó e selecione **Adicionar Conexão**. A partir daqui, você também pode se conectar a um banco de dados em outro servidor, um serviço do SharePoint ou um serviço do Azure.

![Ícone de Conexão de novo Gerenciador do servidor](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Isso abre o **Adicionar Conexão** caixa de diálogo. Aqui, inserimos o nome da instância LocalDB do SQL Server.

![Adicionar Nova Conexão](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Alterar o provedor

Se a fonte de dados não é o desejado, clique o **alteração** botão para escolher uma nova fonte de dados e/ou em um novo provedor de dados do ADO.NET. O novo provedor pode solicitar suas credenciais, dependendo de como você configurou.

![Provedor de dados AD0.NET de alteração](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Testar a conexão

Depois de escolher a fonte de dados, clique em **Conexão de teste**. Se não tiver êxito, você precisará solucionar problemas com base na documentação do fornecedor.

![Testar Conexão](../data-tools/media/raddata-test-connection.png)

Se o teste for bem-sucedido, você está pronto para criar uma *fonte de dados*, que é um termo do Visual Studio que realmente significa uma *modelo de dados* baseado em um banco de dados ou serviço subjacente.

## <a name="see-also"></a>Consulte também

- [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
