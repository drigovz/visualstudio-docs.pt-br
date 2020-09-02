---
title: Inserir novos registros em um banco de dados | Microsoft Docs
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c686a764f42f50a3e59da3e8b37b219ddb7b11c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651556"
---
# <a name="insert-new-records-into-a-database"></a>Inserir novos registros em um banco de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para inserir novos registros em um banco de dados, você pode usar o `TableAdapter.Update` método ou um dos métodos DBDirect do TableAdapter (especificamente o `TableAdapter.Insert` método).

 Se seu aplicativo não usar TableAdapters, você poderá usar objetos de comando (por exemplo,  <xref:System.Data.SqlClient.SqlCommand> ) para inserir novos registros em seu banco de dados.

 Se o seu aplicativo usa conjuntos de dados para armazenar, use o `TableAdapter.Update` método. O `Update` método envia todas as alterações (atualizações, inserções e exclusões) para o banco de dados.

 Se seu aplicativo usar objetos para armazenar dados, ou se você quiser um controle mais preciso sobre a criação de novos registros no banco de dado, use o `TableAdapter.Insert` método.

 Se o TableAdapter não tiver um `Insert` método, significa que o TableAdapter está configurado para usar procedimentos armazenados ou sua `GenerateDBDirectMethods` propriedade é definida como `false` . Tente definir a propriedade do TableAdapter `GenerateDBDirectMethods` para `true` de dentro do designer de conjunto de dados e salve o conjunto de os. Isso irá regenerar o TableAdapter. Se o TableAdapter ainda não tiver um `Insert` método, a tabela provavelmente não fornecerá informações de esquema suficientes para distinguir entre linhas individuais (por exemplo, pode não haver nenhum conjunto de chaves primárias na tabela).

## <a name="insert-new-records-by-using-tableadapters"></a>Inserir novos registros usando TableAdapters
 Os TableAdapters fornecem maneiras diferentes de inserir novos registros em um banco de dados, dependendo dos requisitos do seu aplicativo.

 Se o seu aplicativo usa conjuntos de dados para armazenar dado, você pode simplesmente adicionar novos registros ao desejado <xref:System.Data.DataTable> no DataSet e, em seguida, chamar o `TableAdapter.Update` método. O `TableAdapter.Update` método envia quaisquer alterações no <xref:System.Data.DataTable> banco de dados (incluindo registros modificados e excluídos).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Para inserir novos registros em um banco de dados usando o método TableAdapter. Update

1. Adicione novos registros ao desejado <xref:System.Data.DataTable> criando um novo <xref:System.Data.DataRow> e adicionando-o à <xref:System.Data.DataTable.Rows%2A> coleção. Para obter mais informações, consulte [como: adicionar linhas a uma DataTable](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).

2. Depois que as novas linhas forem adicionadas ao <xref:System.Data.DataTable> , chame o `TableAdapter.Update` método. Você pode controlar a quantidade de dados a serem atualizados passando um inteiro <xref:System.Data.DataSet> , um <xref:System.Data.DataTable> , uma matriz de <xref:System.Data.DataRow> s ou um único <xref:System.Data.DataRow> .

    O código a seguir mostra como adicionar um novo registro a um <xref:System.Data.DataTable> e, em seguida, chamar o `TableAdapter.Update` método para salvar a nova linha no banco de dados. (Este exemplo usa a `Region` tabela no banco de dados Northwind.)

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Se seu aplicativo usa objetos para armazenar dados, você pode usar o `TableAdapter.Insert` método para criar novas linhas diretamente no banco de dado. O `Insert` método aceita os valores individuais para cada coluna como parâmetros. Chamar o método insere um novo registro no banco de dados com os valores de parâmetro passados.

   O procedimento a seguir usa a `Region` tabela no banco de dados Northwind como um exemplo.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Para inserir novos registros em um banco de dados usando o método TableAdapter. Insert

- Chame o método do TableAdapter `Insert` , passando os valores para cada coluna como parâmetros.

    > [!NOTE]
    > Se você não tiver uma instância disponível, crie uma instância do TableAdapter que você deseja usar.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Inserir novos registros usando objetos de comando
 O exemplo a seguir insere novos registros diretamente em um banco de dados usando objetos de comando.

 O procedimento a seguir usa a `Region` tabela no banco de dados Northwind como um exemplo.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Para inserir novos registros em um banco de dados usando objetos de comando

- Crie um novo objeto de comando e, em seguida, defina suas `Connection` `CommandType` Propriedades, e `CommandText` .

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>Segurança do .NET Framework
 Você deve ter acesso ao banco de dados ao qual está tentando se conectar, bem como permissão para executar inserções na tabela desejada.

## <a name="see-also"></a>Consulte Também
 [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)
