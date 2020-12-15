---
title: 'Como: imprimir planilhas programaticamente'
description: Saiba como você pode usar o Visual Studio para imprimir programaticamente qualquer planilha em uma pasta de trabalho do Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 356c47ec3275c1442082f367dd08fe6901f9c0a3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523757"
---
# <a name="how-to-programmatically-print-worksheets"></a>Como: imprimir planilhas programaticamente

Você pode imprimir qualquer planilha em uma pasta de trabalho.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Imprimir uma planilha em uma personalização no nível do documento

### <a name="to-print-a-worksheet"></a>Para imprimir uma planilha

1. Chame o `PrintOut` método de `Sheet1` , solicite duas cópias e visualize o documento antes de imprimir.

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   O <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> método permite que você exiba o objeto especificado na janela de **visualização de impressão** . O código a seguir pressupõe que você tenha um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host chamado `Sheet1` .

### <a name="to-preview-a-page-before-printing"></a>Para visualizar uma página antes da impressão

1. Chame o <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> método da planilha.

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Imprimir uma planilha em um suplemento do VSTO

### <a name="to-print-a-worksheet"></a>Para imprimir uma planilha

1. Chame o <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> método da planilha ativa, solicite duas cópias e visualize o documento antes de imprimir.

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   O <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> método permite que você exiba o objeto especificado na janela de **visualização de impressão** .

### <a name="to-preview-a-page-before-printing"></a>Para visualizar uma página antes da impressão

1. Chame o <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> método da planilha ativa.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Veja também

- [Trabalhar com planilhas](../vsto/working-with-worksheets.md)
- [Como: verificar a ortografia em planilhas programaticamente](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Item de host de planilha](../vsto/worksheet-host-item.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
