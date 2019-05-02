---
title: 'Como: Verificar a ortografia em planilhas de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: feb284657932a0c20cd785b14db5e2b3de9366f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575553"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Como: Verificar a ortografia em planilhas de forma programática
  Você pode verificar a ortografia de palavras em uma planilha programaticamente. O **ortografia** caixa de diálogo aparece automaticamente se há qualquer as palavras escritas incorretamente na planilha.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Para verificar a ortografia em uma planilha em uma personalização no nível de documento

1. Chamar o <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> método da planilha.

     [!code-csharp[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Para verificar a ortografia em uma planilha em um suplemento do VSTO

1. Chamar o <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> método da planilha ativa.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]

## <a name="see-also"></a>Consulte também
- [Trabalhar com planilhas](../vsto/working-with-worksheets.md)
- [Como: Executar cálculos do Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Controle NamedRange](../vsto/namedrange-control.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
