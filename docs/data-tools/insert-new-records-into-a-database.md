---
title: Inserir novos registros em um banco de dados
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aaca23e6aa81fab958fc813fa5e2331f8906a562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648312"
---
# <a name="insert-new-records-into-a-database"></a>Inserir novos registros em um banco de dados

Para inserir novos registros em um banco de dados, você pode usar o método `TableAdapter.Update` ou um dos métodos DBDirect do TableAdapter (especificamente o método `TableAdapter.Insert`). Para obter mais informações, consulte [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Se o seu aplicativo não usar TableAdapters, você poderá usar objetos de comando (por exemplo, <xref:System.Data.SqlClient.SqlCommand>) para inserir novos registros em seu banco de dados.

Se o seu aplicativo usa conjuntos de dados para armazenar, use o método `TableAdapter.Update`. O método `Update` envia todas as alterações (atualizações, inserções e exclusões) para o banco de dados.

Se seu aplicativo usa objetos para armazenar dados, ou se você quiser um controle mais preciso sobre a criação de novos registros no banco de dado, use o método `TableAdapter.Insert`.

Se o TableAdapter não tiver um método `Insert`, significa que o TableAdapter está configurado para usar procedimentos armazenados ou sua propriedade `GenerateDBDirectMethods` está definida como `false`. Tente definir a propriedade `GenerateDBDirectMethods` do TableAdapter como `true` de dentro do **Designer de conjunto de dados**e, em seguida, salve o conjunto de os. Isso irá regenerar o TableAdapter. Se o TableAdapter ainda não tiver um método `Insert`, a tabela provavelmente não fornecerá informações de esquema suficientes para distinguir entre linhas individuais (por exemplo, pode não haver nenhuma chave primária definida na tabela).

## <a name="insert-new-records-by-using-tableadapters"></a>Inserir novos registros usando TableAdapters

Os TableAdapters fornecem maneiras diferentes de inserir novos registros em um banco de dados, dependendo dos requisitos do seu aplicativo.

Se o seu aplicativo usa conjuntos de dados para armazenar, você pode simplesmente adicionar novos registros ao <xref:System.Data.DataTable> desejado no DataSet e, em seguida, chamar o método `TableAdapter.Update`. O método `TableAdapter.Update` envia quaisquer alterações no <xref:System.Data.DataTable> para o banco de dados (incluindo registros modificados e excluídos).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Para inserir novos registros em um banco de dados usando o método TableAdapter. Update

1. Adicione novos registros ao <xref:System.Data.DataTable> desejado criando um novo <xref:System.Data.DataRow> e adicionando-o à coleção de <xref:System.Data.DataTable.Rows%2A>.

2. Depois que as novas linhas forem adicionadas à <xref:System.Data.DataTable>, chame o método `TableAdapter.Update`. Você pode controlar a quantidade de dados a serem atualizados passando uma <xref:System.Data.DataSet> inteira, uma <xref:System.Data.DataTable>, uma matriz de <xref:System.Data.DataRow>s ou uma única <xref:System.Data.DataRow>.

   O código a seguir mostra como adicionar um novo registro a um <xref:System.Data.DataTable> e, em seguida, chamar o método `TableAdapter.Update` para salvar a nova linha no banco de dados. (Este exemplo usa a tabela `Region` no banco de dados Northwind.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Para inserir novos registros em um banco de dados usando o método TableAdapter. Insert

Se seu aplicativo usa objetos para armazenar dados, você pode usar o método `TableAdapter.Insert` para criar novas linhas diretamente no banco de dado. O método `Insert` aceita os valores individuais para cada coluna como parâmetros. Chamar o método insere um novo registro no banco de dados com os valores de parâmetro passados.

- Chame o método `Insert` do TableAdapter, passando os valores de cada coluna como parâmetros.

O procedimento a seguir demonstra como usar o método `TableAdapter.Insert` para inserir linhas. Este exemplo insere dados na tabela `Region` no banco de dados Northwind.

> [!NOTE]
> Se você não tiver uma instância disponível, crie uma instância do TableAdapter que você deseja usar.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Inserir novos registros usando objetos de comando

Você pode inserir novos registros diretamente em um banco de dados usando objetos de comando.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Para inserir novos registros em um banco de dados usando objetos de comando

- Crie um novo objeto de comando e, em seguida, defina suas propriedades `Connection`, `CommandType` e `CommandText`.

O exemplo a seguir demonstra a inserção de registros em um banco de dados usando o objeto Command. Ele insere dados na tabela `Region` no banco de dados Northwind.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>Segurança do .NET

Você deve ter acesso ao banco de dados ao qual está tentando se conectar, bem como permissão para executar inserções na tabela desejada.

## <a name="see-also"></a>Consulte também

- [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)