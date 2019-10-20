---
title: Como salvar dados usando uma transação
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cfb03944743609d20d14f6104e5fadd529a5cfa6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641305"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Como salvar dados usando uma transação

Você salva dados em uma transação usando o namespace <xref:System.Transactions>. Use o objeto <xref:System.Transactions.TransactionScope> para participar de uma transação que é gerenciada automaticamente para você.

Os projetos não são criados com uma referência ao assembly *System. Transactions* , portanto, você precisa adicionar manualmente uma referência a projetos que usam transações.

A maneira mais fácil de implementar uma transação é instanciar um objeto <xref:System.Transactions.TransactionScope> em uma instrução `using`. (Para obter mais informações, consulte [instrução using](/dotnet/visual-basic/language-reference/statements/using-statement)e [instrução using](/dotnet/csharp/language-reference/keywords/using-statement).) O código que é executado dentro da instrução `using` participa da transação.

Para confirmar a transação, chame o método <xref:System.Transactions.TransactionScope.Complete%2A> como a última instrução no bloco Using.

Para reverter a transação, acione uma exceção antes de chamar o método <xref:System.Transactions.TransactionScope.Complete%2A>.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Para adicionar uma referência ao System. Transactions. dll

1. No menu **projeto** , selecione **Adicionar referência**.

2. Na guia **.net** (**SQL Server** guia para projetos SQL Server), selecione **System. Transactions**e, em seguida, selecione **OK**.

     Uma referência a *System. Transactions. dll* é adicionada ao projeto.

## <a name="to-save-data-in-a-transaction"></a>Para salvar dados em uma transação

- Adicione código para salvar dados dentro da instrução using que contém a transação. O código a seguir mostra como criar e instanciar um objeto <xref:System.Transactions.TransactionScope> em uma instrução Using:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Consulte também

- [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)
- [Passo a passo: salvar dados em uma transação](../data-tools/save-data-in-a-transaction.md)