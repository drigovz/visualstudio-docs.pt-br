---
title: Acessar diretamente o banco de dados com um TableAdapter | Microsoft Docs
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
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58500e59a624dac55824033b8b9667754a9040c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657368"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Acessar o banco de dados diretamente com um TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Além do `InsertCommand`, `UpdateCommand` e `DeleteCommand`, os TableAdapters são criados com métodos que podem ser executados diretamente no banco de dados. Esses métodos (`TableAdapter.Insert`, `TableAdapter.Update` e `TableAdapter.Delete`) podem ser chamados para manipular dados diretamente no banco de dado.

 Se você não quiser criar esses métodos diretos, defina a propriedade `GenerateDbDirectMethods` do TableAdapter como `false` na janela **Propriedades** . Se qualquer consulta for adicionada a um TableAdapter além da consulta principal do TableAdapter, elas serão consultas autônomas que não geram esses métodos DbDirect.

## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly a um banco de dados
 Chame o método DbDirect do TableAdapter que executa a tarefa que você está tentando realizar.

#### <a name="to-insert-new-records-directly-into-a-database"></a>Para inserir novos registros diretamente em um banco de dados

- Chame o método `Insert` do TableAdapter, passando os valores de cada coluna como parâmetros. O procedimento a seguir usa a tabela `Region` no banco de dados Northwind como um exemplo.

    > [!NOTE]
    > Se você não tiver uma instância disponível, crie uma instância do TableAdapter que você deseja usar.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

#### <a name="to-update-records-directly-in-a-database"></a>Para atualizar registros diretamente em um banco de dados

- Chame o método `Update` do TableAdapter, passando os valores novos e originais para cada coluna como parâmetros.

    > [!NOTE]
    > Se você não tiver uma instância disponível, crie uma instância do TableAdapter que você deseja usar.

     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]

#### <a name="to-delete-records-directly-from-a-database"></a>Para excluir registros diretamente de um banco de dados

- Chame o método `Delete` do TableAdapter, passando os valores de cada coluna como parâmetros do método `Delete`. O procedimento a seguir usa a tabela `Region` no banco de dados Northwind como um exemplo.

    > [!NOTE]
    > Se você não tiver uma instância disponível, crie uma instância do TableAdapter que você deseja usar.

     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]

## <a name="see-also"></a>Consulte também
 [Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
