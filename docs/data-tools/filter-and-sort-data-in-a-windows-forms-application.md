---
title: Filtrar e classificar dados em um aplicativo do Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 596397cc22cf0f0134463256c0861127dcfb81e1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586608"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrar e classificar dados em um aplicativo do Windows Forms

Você filtra os dados definindo a propriedade <xref:System.Windows.Forms.BindingSource.Filter%2A> como uma expressão de cadeia de caracteres que retorna os registros desejados.

Você classifica os dados definindo a propriedade <xref:System.Windows.Forms.BindingSource.Sort%2A> como o nome da coluna na qual você deseja classificar; Acrescente `DESC` para classificar em ordem decrescente ou acrescentar `ASC` para classificar em ordem crescente.

> [!NOTE]
> Se o seu aplicativo não usar <xref:System.Windows.Forms.BindingSource> componentes, você poderá filtrar e classificar dados usando <xref:System.Data.DataView> objetos. Para obter mais informações, consulte [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Para filtrar dados usando um componente BindingSource

- Defina a propriedade <xref:System.Windows.Forms.BindingSource.Filter%2A> como a expressão que você deseja retornar. Por exemplo, o código a seguir retorna aos clientes um `CompanyName` que começa com "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Para classificar dados usando um componente BindingSource

- Defina a propriedade <xref:System.Windows.Forms.BindingSource.Sort%2A> como a coluna que você deseja classificar. Por exemplo, o código a seguir classifica os clientes na coluna `CompanyName` em ordem decrescente:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Veja também

- [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
