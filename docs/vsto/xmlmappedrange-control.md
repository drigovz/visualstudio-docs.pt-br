---
title: Controle XmlMappedRange
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01417d9c08491edc882f7f758bb36e6184500e52
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985369"
---
# <a name="xmlmappedrange-control"></a>Controle XmlMappedRange
  O controle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> é um intervalo que é criado somente quando um elemento de esquema não repetitivo é mapeado em uma célula no Microsoft Office Excel. Por exemplo, quando o atributo `maxOccurs` de um elemento de esquema é igual a 1. Depois que o Visual Studio cria o intervalo mapeado XML, você pode programá-lo diretamente sem ter que atravessar o modelo de objeto do Excel. Você só pode excluir um controle de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> no Excel quando o mapeamento de elemento é removido.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Associar dados ao controle
 Um controle de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> dá suporte à associação a um único campo de dados (vinculação de dados simples). O controle <xref:Microsoft.Office.Tools.Excel.ListObject> pode dar suporte à ligação de dados complexa e é criado automaticamente quando um elemento de esquema repetitivo é mapeado em uma célula. Para obter mais informações, consulte o [controle ListObject](../vsto/listobject-control.md).

 O controle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> está associado a uma fonte de dados usando a propriedade <xref:System.Windows.Forms.Control.DataBindings%2A>. Quando um <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> é adicionado a uma célula de planilha, o Visual Studio gera automaticamente um conjunto de dados a partir dos dados nas células mapeadas e associa o controle a esse conjunto de dados. A propriedade de associação de dados padrão da <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> é <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.

 Se os dados no conjunto de dados vinculados forem atualizados por meio de qualquer mecanismo, o controle de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> refletirá as alterações.

## <a name="formatting"></a>Formatação
 Você pode aplicar a mesma formatação a um controle de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> que você pode aplicar a um <xref:Microsoft.Office.Interop.Excel.Range>. Isso inclui bordas, fontes, formato de número e estilos.

## <a name="events"></a>Eventos
 Os eventos disponíveis para o controle de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> são:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Consulte também
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Como: adicionar controles XMLMappedRange a planilhas](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Como Mapear esquemas para planilhas dentro do Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
