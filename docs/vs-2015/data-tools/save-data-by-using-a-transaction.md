---
title: Salvar dados usando uma transação | Microsoft Docs
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
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85f3584073523e748168faf569aa918ba912fbf8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652830"
---
# <a name="save-data-by-using-a-transaction"></a>Salvar dados usando uma transação
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você salva dados em uma transação usando o namespace <xref:System.Transactions>. Use o objeto <xref:System.Transactions.TransactionScope> para participar de uma transação que é gerenciada automaticamente para você.

 Os projetos não são criados com uma referência ao assembly System. Transactions, portanto, você precisa adicionar manualmente uma referência a projetos que usam transações.

> [!NOTE]
> O namespace <xref:System.Transactions> tem suporte no Windows 2000 ou posterior.

 A maneira mais fácil de implementar uma transação é instanciar um objeto <xref:System.Transactions.TransactionScope> em uma instrução `using`. (Para obter mais informações, consulte [instrução using](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)e [instrução using](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) O código que é executado dentro da instrução `using` participa da transação.

 Para confirmar a transação, chame o método <xref:System.Transactions.TransactionScope.Complete%2A> como a última instrução no bloco Using.

 Para reverter a transação, acione uma exceção antes de chamar o método <xref:System.Transactions.TransactionScope.Complete%2A>.

 Para obter mais informações, consulte [salvar dados em uma transação](../data-tools/save-data-in-a-transaction.md).

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Para adicionar uma referência à DLL System. Transactions

1. No menu **projeto** , selecione **Adicionar referência**.

2. Na guia **.net** (**SQL Server** guia para projetos SQL Server), selecione **System. Transactions**e, em seguida, selecione **OK**.

     Uma referência a System. Transactions. dll é adicionada ao projeto.

### <a name="to-save-data-in-a-transaction"></a>Para salvar dados em uma transação

- Adicione código para salvar dados dentro da instrução using que contém a transação. O código a seguir mostra como criar e instanciar um objeto <xref:System.Transactions.TransactionScope> em uma instrução Using:

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>Consulte também
 [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)
