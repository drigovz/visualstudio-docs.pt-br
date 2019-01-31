---
title: 'Como: Salvar dados usando uma transação'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ecf63cc03af13cadb5791e2f0f5a058feedb8418
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934069"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Como: Salvar dados usando uma transação

Salvar dados em uma transação usando o <xref:System.Transactions> namespace. Use o <xref:System.Transactions.TransactionScope> objeto participe de uma transação que é gerenciada automaticamente para você.

Projetos não são criados com uma referência para o *System. Transactions* assembly, portanto, você precisa adicionar manualmente uma referência a projetos que usam transações.

A maneira mais fácil para implementar uma transação é criar uma instância de um <xref:System.Transactions.TransactionScope> do objeto em um `using` instrução. (Para obter mais informações, consulte [usando a instrução](/dotnet/visual-basic/language-reference/statements/using-statement), e [usando a instrução](/dotnet/csharp/language-reference/keywords/using-statement).) O código executado dentro de `using` instrução participa na transação.

Para confirmar a transação, chame o <xref:System.Transactions.TransactionScope.Complete%2A> bloquear o método como a última instrução em uso.

Para reverter a transação, lançar uma exceção antes de chamar o <xref:System.Transactions.TransactionScope.Complete%2A> método.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Para adicionar uma referência para a Transactions

1.  Sobre o **Project** menu, selecione **adicionar referência**.

2.  Sobre o **.NET** guia (**SQL Server** guia para projetos do SQL Server), selecione **System. Transactions**e, em seguida, selecione **Okey**.

     Uma referência a *Transactions* é adicionado ao projeto.

## <a name="to-save-data-in-a-transaction"></a>Para salvar dados em uma transação

-   Adicione código para salvar os dados dentro da usando instrução que contém a transação. O código a seguir mostra como criar e instanciar um <xref:System.Transactions.TransactionScope> objeto em um usando instrução:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Consulte também

- [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)
- [Passo a passo: Salvando dados em uma transação](../data-tools/save-data-in-a-transaction.md)