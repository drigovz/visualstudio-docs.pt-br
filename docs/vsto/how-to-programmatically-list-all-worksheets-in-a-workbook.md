---
title: 'Como: programaticamente listar todas as planilhas em uma pasta de trabalho'
description: Saiba como você pode listar todas as planilhas de forma programática em uma pasta de trabalho do Microsoft Excel usando o Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1446a4323ac190ede301e3a1cc55ccf1cae3b491
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885307"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Como: programaticamente listar todas as planilhas em uma pasta de trabalho
  A <xref:Microsoft.Office.Interop.Excel.Workbook> classe fornece um <xref:Microsoft.Office.Interop.Excel.Worksheets> objeto. Este objeto contém uma coleção de todos os <xref:Microsoft.Office.Interop.Excel.Worksheet> objetos na pasta de trabalho.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Para listar todas as planilhas existentes em uma pasta de trabalho em uma personalização em nível de documento

1. Iterar pela <xref:Microsoft.Office.Interop.Excel.Worksheets> coleção e enviar o nome de cada planilha para um deslocamento de célula de <xref:Microsoft.Office.Tools.Excel.NamedRange> um controle.

     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Para listar todas as planilhas existentes em uma pasta de trabalho em um suplemento do VSTO

1. Iterar pela <xref:Microsoft.Office.Interop.Excel.Worksheets> coleção e enviar o nome de cada planilha para um deslocamento de célula de <xref:Microsoft.Office.Interop.Excel.Range> um objeto.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>Confira também
- [Trabalhar com planilhas](../vsto/working-with-worksheets.md)
- [Como: adicionar programaticamente novas planilhas a pastas de trabalho](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Como: mover planilhas programaticamente dentro de pastas de trabalho](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
