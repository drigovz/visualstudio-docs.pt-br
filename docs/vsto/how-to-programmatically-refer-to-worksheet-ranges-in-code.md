---
title: 'Como: Por meio de programação se referir a intervalos de planilhas em código'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be71d18b7fa0b3cc9dba8a27c6c462d5ea1a2434
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608429"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Como: Por meio de programação se referir a intervalos de planilhas em código
  Usar um processo semelhante para referir-se ao conteúdo de um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ou um objeto de intervalo do Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usar um controle NamedRange
 O exemplo a seguir adiciona um <xref:Microsoft.Office.Tools.Excel.NamedRange> para uma planilha e, em seguida, adiciona texto para a célula no intervalo.

### <a name="to-refer-to-a-namedrange-control"></a>Para se referir a um controle NamedRange

1.  Atribuir uma cadeia de caracteres para o <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriedade do <xref:Microsoft.Office.Tools.Excel.NamedRange> controle. Esse código deve ser colocado em uma classe de folha, não no `ThisWorkbook` classe.

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>Use o native intervalos do Excel
 O exemplo a seguir adiciona um intervalo do Excel nativo a uma planilha e, em seguida, adiciona texto para a célula no intervalo.

### <a name="to-refer-to-a-native-range-object"></a>Para se referir a um objeto range nativo

1.  Atribuir uma cadeia de caracteres para o <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> propriedade do intervalo.

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>Consulte também
- [Trabalhar com intervalos](../vsto/working-with-ranges.md)
- [Como: Verificar a ortografia em planilhas de forma programática](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Como: Aplicar estilos a intervalos em pastas de trabalho programaticamente](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Como: Por meio de programação automaticamente preencher intervalos com dados alterados em incrementos](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Como: Pesquisar texto em intervalos de planilhas de forma programática](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [Controle NamedRange](../vsto/namedrange-control.md)
- [Visão geral dos controles de host e de itens de host](../vsto/host-items-and-host-controls-overview.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
