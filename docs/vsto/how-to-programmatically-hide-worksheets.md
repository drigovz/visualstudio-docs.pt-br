---
title: 'Como: Ocultar planilhas programaticamente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f1fca54350900b2ed252efc324308d1168c6da53
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101100"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Como: Ocultar planilhas programaticamente
  Você pode mostrar ou ocultar qualquer planilha em uma pasta de trabalho. Para ocultar uma planilha, use o item de host da planilha ou acessar a planilha usando a coleção de planilhas da pasta de trabalho.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Use o item de host da planilha
 Se a planilha foi adicionada em tempo de design em uma personalização no nível de documento, use o <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> propriedade para ocultar a planilha especificada.

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Para ocultar uma planilha usando um item de host da planilha

1. Defina a <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> propriedade do `Sheet1` item de host para o <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> valor de enumeração.

     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usar a coleção de planilhas da pasta de trabalho do Excel
 Acessar planilhas por meio do Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> coleção nos seguintes casos:

- Você deseja ocultar uma planilha em um suplemento do VSTO.

- A planilha que você deseja ocultar foi criada em tempo de execução em uma personalização no nível de documento.

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Para ocultar uma planilha usando a coleção de planilhas da pasta de trabalho do Excel

1. Defina as <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> propriedade da planilha para o <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> valor de enumeração.

     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]

## <a name="see-also"></a>Consulte também
- [Trabalhar com planilhas](../vsto/working-with-worksheets.md)
- [Como: Excluir planilhas de pastas de trabalho de forma programática](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Como: Mover planilhas em pastas de trabalho de forma programática](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Como: Proteger planilhas programaticamente](../vsto/how-to-programmatically-protect-worksheets.md)
- [Visão geral dos controles de host e de itens de host](../vsto/host-items-and-host-controls-overview.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
