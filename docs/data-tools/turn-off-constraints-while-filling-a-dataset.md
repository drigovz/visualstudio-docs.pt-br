---
title: Desabilitar restrições ao preencher um conjunto de dados
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9aca29de7e9c5a01e0c2caad2c42015cd31b3f75
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565180"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Desabilitar restrições ao preencher um conjunto de dados

Se um conjunto de dados contiver restrições (como restrições de chave estrangeira), eles poderão gerar erros relacionados a ordem de operações que são executadas com o conjunto de dados. Por exemplo, carregamento de registros filho antes de carregar relacionadas a registros pai podem violar uma restrição e causar um erro. Assim que você carrega um registro filho, a restrição verifica o registro pai relacionado e gera um erro.

Se não houver nenhum mecanismo para permitir a suspensão de restrição temporária, um erro seria gerado toda vez que você tentou carregar um registro na tabela filho. Outra maneira para suspender todas as restrições em um conjunto de dados é com o <xref:System.Data.DataRow.BeginEdit%2A>, e <xref:System.Data.DataRow.EndEdit%2A> propriedades.

> [!NOTE]
> Eventos de validação (por exemplo, <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging>) não serão gerados quando as restrições estão desativadas.

## <a name="to-suspend-update-constraints-programmatically"></a>Para suspender restrições de atualização por meio de programação

- O exemplo a seguir mostra como desativar temporariamente a restrição de verificação em um conjunto de dados:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Para suspender restrições de atualização usando o Designer de conjunto de dados

1. Abra o conjunto de dados no **Designer de Conjunto de Dados**. Para obter mais informações, confira [Passo a passo: Criando um conjunto de dados no Designer de conjunto de dados](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. No **propriedades** janela, defina as <xref:System.Data.DataSet.EnforceConstraints%2A> propriedade `false`.

## <a name="see-also"></a>Consulte também

- [Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relacionamentos em conjuntos de dados](../data-tools/relationships-in-datasets.md)