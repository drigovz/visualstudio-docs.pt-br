---
title: Atualizar arquivos. MDF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 5b26b8cd9d955309e3be0e17e975bfdeb242e475
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621404"
---
# <a name="upgrade-mdf-files"></a>Atualizar arquivos .mdf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico descreve as opções para atualizar seu arquivo de banco de dados (. MDF) depois de instalar uma versão mais recente do Visual Studio. Ele inclui instruções para as seguintes tarefas:

- Atualizar um arquivo de banco de dados para usar uma versão mais recente do SQL Server Express LocalDB

- Atualizar um arquivo de banco de dados para usar uma versão mais recente do SQL Server Express

- Trabalhar com um arquivo de banco de dados no Visual Studio, mas manter a compatibilidade com uma versão mais antiga do SQL Server Express ou LocalDB

- Fazer SQL Server Express o mecanismo de banco de dados padrão

  Você pode usar o Visual Studio para abrir um projeto que contém um arquivo de banco de dados (. MDF) que foi criado usando uma versão mais antiga do SQL Server Express ou LocalDB. No entanto, para continuar a desenvolver seu projeto no Visual Studio, você deve ter essa versão do SQL Server Express ou LocalDB instalada no mesmo computador que o Visual Studio, ou você deve atualizar o arquivo de banco de dados. Se você atualizar o arquivo de banco de dados, não poderá acessá-lo usando versões mais antigas do SQL Server Express ou LocalDB.

  Você também pode ser solicitado a atualizar um arquivo de banco de dados criado por meio de uma versão anterior do SQL Server Express ou LocalDB se a versão do arquivo não for compatível com a instância do SQL Server Express ou do LocalDB que está atualmente instalado. Para resolver o problema, o Visual Studio solicitará que você atualize o arquivo.

> [!IMPORTANT]
> Recomendamos que você faça backup do arquivo de banco de dados antes de atualizá-lo.

> [!WARNING]
> Se você atualizar um arquivo. MDF que foi criado no LocalDB 2014 (V12) 32 bit para LocalDB 2016 (v13), não será possível abrir o arquivo novamente na versão de 32 bits do LocalDB.  Na atualização 2, LocalDB v13 é de apenas 64 bits.

 Antes de atualizar um banco de dados, considere os seguintes critérios:

- Não atualize se você quiser trabalhar em seu projeto em uma versão mais antiga e uma versão mais recente do Visual Studio.

- Não atualize se seu aplicativo for usado em ambientes que usam SQL Server Express em vez de LocalDB.

- Não atualize se seu aplicativo usar conexões remotas, porque o LocalDB não as aceita.

- Não atualize se seu aplicativo depender de Serviços de Informações da Internet (IIS).

- Considere atualizar se você deseja testar aplicativos de banco de dados em um ambiente de área restrita, mas não deseja administrar um banco de dados.

### <a name="to-upgrade-a-database-file"></a>Para atualizar um arquivo de banco de dados

1. Em **Gerenciador de servidores**, selecione o botão **conectar ao banco de dados** .

2. Na caixa de diálogo **Adicionar conexão** , especifique as seguintes informações:

   - **Fonte de dados**: `Microsoft SQL Server (SqlClient)`

   - **Nome do Servidor**:

       - Para usar a versão padrão: `(localdb)\MSSQLLocalDB` .  Isso especificará o ProjectV12 ou o ProjectV13, dependendo de qual versão do Visual Studio está instalada e quando a primeira instância de LocalDB foi criada. O nó **MSSQLLocalDB** no **pesquisador de objetos do SQL Server** mostra a qual versão ele está apontando.

       - Para usar uma versão específica: `(localdb)\ProjectsV12` ou `(localdb)\ProjectsV13` , em que V12 é LocalDB 2014 e v13 é LocalDB 2016.

   - **Anexar um arquivo do banco de dados**: O caminho físico da réplica primária mdf arquivo.

   - **Nome lógico**: O nome que você deseja usar com o arquivo.

3. Selecione o botão **OK** .

4. Quando for solicitado, selecione o botão **Sim** para atualizar o arquivo.

   O banco de dados é atualizado, é anexado ao mecanismo de banco de dados LocalDB e não é mais compatível com a versão mais antiga do LocalDB.

   Você também pode modificar uma conexão SQL Server Express para usar o LocalDB abrindo o menu de atalho para a conexão e, em seguida, selecionando **Modificar conexão**. Na caixa de diálogo **Modificar conexão** , altere o nome do servidor para `(LocalDB)\MSSQLLocalDB` . Na caixa de diálogo **Propriedades avançadas** , verifique se a **instância do usuário** está definida como **false**.

### <a name="to-upgrade-to-a-newer-version-of-sql-server-express"></a>Para atualizar para uma versão mais recente do SQL Server Express

1. No menu de atalho para a conexão com o banco de dados, selecione **Modificar conexão**.

2. Na caixa de diálogo **Modificar conexão** , selecione o botão **avançado** .

3. Na caixa de diálogo **Propriedades avançadas** , selecione o botão **OK** sem alterar o nome do servidor.

   O arquivo de banco de dados é atualizado para corresponder à versão atual do SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Para trabalhar com o banco de dados no Visual Studio, mas manter a compatibilidade com SQL Server Express

- No Visual Studio, abra o projeto sem atualizá-lo.

  - Para executar o projeto, selecione a tecla F5.

  - Para editar o banco de dados, abra o arquivo. mdf em **Gerenciador de soluções**e expanda o nó em **Gerenciador de servidores** para trabalhar com seu banco de dados.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Para fazer SQL Server Express o mecanismo de banco de dados padrão

1. Na barra de menus, selecione **Ferramentas** > **Opções**.

2. Na caixa de diálogo **Opções** , expanda as opções de **ferramentas de dados** e selecione o nó **conexões de dados** .

3. Na caixa de texto **nome da instância do SQL Server** , especifique o nome da instância do SQL Server Express ou LocalDB que você deseja usar. Se a instância não for nomeada, especifique `.\SQLEXPRESS or (localdb)\MSSQLLocalDB` .

4. Selecione o botão **OK** .

   SQL Server Express será o mecanismo de banco de dados padrão para seus aplicativos.
