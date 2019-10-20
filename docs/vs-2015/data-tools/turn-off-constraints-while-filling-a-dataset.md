---
title: Desativar restrições ao preencher um conjunto de uma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6646f669bf2c465d8e0f705f8fba956b979952ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667164"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Desabilitar restrições ao preencher um conjunto de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se um conjunto de um dataset contiver restrições (como restrições Foreign-Key), theycan gerará erros relacionados à ordem das operações executadas no conjunto de um. Por exemplo, carregar registros filho antes que os registros pai do loadingrelated possam violar uma restrição e causar um erro. Assim que você carregar um registro filho, a restrição verificará o registro pai relacionado e gerará um erro.

 Se não houver nenhum mecanismo para permitir a suspensão de restrição temporária, um erro será gerado toda vez que você tentar carregar um registro na tabela filho. Outra maneira de suspender todas as restrições em um conjunto de um DataSet é com as propriedades <xref:System.Data.DataRow.BeginEdit%2A> e <xref:System.Data.DataRow.EndEdit%2A>.

> [!NOTE]
> Eventos de validação (por exemplo, <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging>) não serão gerados quando as restrições forem desativadas.

### <a name="to-suspend-update-constraints-programmatically"></a>Para suspender restrições de atualização programaticamente

- O exemplo a seguir mostra como desativar temporariamente a verificação de restrição em um conjunto de uma:

     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]

### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Para suspender restrições de atualização usando o Designer de Conjunto de Dados

1. Abra o conjunto de seus conjuntos de Designer de Conjunto de Dados. Para obter mais informações, consulte [como: abrir um conjunto de dados no designer de conjunto de dados](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Na janela **Propriedades** , defina a propriedade <xref:System.Data.DataSet.EnforceConstraints%2A> como `false`.

## <a name="see-also"></a>Consulte também
 [Preencher conjuntos de valores usando relações do TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) [em conjuntos de](../data-tools/relationships-in-datasets.md) os
