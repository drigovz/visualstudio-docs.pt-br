---
title: 'Como: adicionar programaticamente novas planilhas a pastas de trabalho'
description: Saiba como você pode criar programaticamente uma planilha e, em seguida, adicionar a planilha à coleção de planilhas na pasta de trabalho.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3397b2ad8f656a7ada82ce0be17dcf21064d0ee3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96843978"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Como: adicionar programaticamente novas planilhas a pastas de trabalho
  Você pode criar programaticamente uma planilha e, em seguida, adicionar a planilha à coleção de planilhas na pasta de trabalho.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Para adicionar uma nova planilha a uma pasta de trabalho em uma personalização em nível de documento

1. Use o <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> método da <xref:Microsoft.Office.Interop.Excel.Sheets> coleção.

     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]

     A nova planilha é um <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto nativo e não um item de host. Se você quiser adicionar um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host, deverá adicionar a planilha em tempo de design.

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Para adicionar uma nova planilha a uma pasta de trabalho em um suplemento do VSTO

1. Use o <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> método da <xref:Microsoft.Office.Interop.Excel.Sheets> coleção.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]

     A nova planilha é um <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto nativo e não um item de host. Você também pode gerar um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host a partir do <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto nativo. Para obter mais informações, consulte [estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Confira também
- [Trabalhar com planilhas](../vsto/working-with-worksheets.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Como: excluir programaticamente planilhas de pastas de trabalho](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Como: selecionar planilhas programaticamente](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
