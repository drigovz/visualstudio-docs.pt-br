---
title: 'Como: verificar a ortografia em planilhas programaticamente'
description: Saiba como você pode verificar a ortografia de palavras de forma programática em uma planilha do Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94361db98c78a2767680d2358d2153b63df9571a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867978"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Como: verificar a ortografia em planilhas programaticamente
  Você pode verificar a ortografia de palavras de forma programática em uma planilha. A caixa de diálogo **ortografia** será exibida automaticamente se houver palavras escritas incorretamente na planilha.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Para verificar a ortografia em uma planilha em uma personalização no nível do documento

1. Chame o <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> método da planilha.

     [!code-csharp[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Para verificar a ortografia em uma planilha em um suplemento do VSTO

1. Chame o <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> método da planilha ativa.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]

## <a name="see-also"></a>Confira também
- [Trabalhar com planilhas](../vsto/working-with-worksheets.md)
- [Como executar cálculos do Excel programaticamente](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Controle NamedRange](../vsto/namedrange-control.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
