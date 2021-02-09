---
title: Filtrar e classificar dados em um aplicativo do Windows Forms
description: Filtrar e classificar dados em um aplicativo Windows Forms. Defina a propriedade de filtro para uma expressão de cadeia de caracteres que retorne os registros desejados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b1708d6871f1acdf437895563d9b5a39dbe93f21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858846"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrar e classificar dados em um aplicativo do Windows Forms

Você filtra os dados definindo a <xref:System.Windows.Forms.BindingSource.Filter%2A> propriedade como uma expressão de cadeia de caracteres que retorna os registros desejados.

Você classifica os dados definindo a <xref:System.Windows.Forms.BindingSource.Sort%2A> propriedade como o nome da coluna na qual você deseja classificar; acrescentar `DESC` para classificar em ordem decrescente ou acrescentar `ASC` para classificar em ordem crescente.

> [!NOTE]
> Se o seu aplicativo não usar <xref:System.Windows.Forms.BindingSource> componentes, você poderá filtrar e classificar dados usando <xref:System.Data.DataView> objetos. Para obter mais informações, consulte [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Para filtrar dados usando um componente BindingSource

- Defina a <xref:System.Windows.Forms.BindingSource.Filter%2A> propriedade para a expressão que você deseja retornar. Por exemplo, o código a seguir retorna clientes com um `CompanyName` que começa com "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Para classificar dados usando um componente BindingSource

- Defina a <xref:System.Windows.Forms.BindingSource.Sort%2A> propriedade para a coluna que você deseja classificar. Por exemplo, o código a seguir classifica os clientes na `CompanyName` coluna em ordem decrescente:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Consulte também

- [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
