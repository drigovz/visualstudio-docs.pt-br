---
title: 'Como: Executar cálculos do Excel'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd6562a48a66c1c73cd281fb4510e2df737f6a04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955674"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Como: Executar cálculos do Excel
  Usar um processo semelhante para executar cálculos em um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ou um objeto de intervalo do Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Executar cálculos em um controle NamedRange
 O exemplo a seguir cria um <xref:Microsoft.Office.Tools.Excel.NamedRange> na célula A1 e, em seguida, calcula a célula. Esse código deve ser colocado em uma classe de folha, não no `ThisWorkbook` classe.

### <a name="to-run-calculations-in-a-namedrange-control"></a>Para executar cálculos em um controle NamedRange

1. Crie o intervalo nomeado.

     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]

2. Chamar o <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> método do intervalo especificado.

     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]

## <a name="run-calculations-in-a-native-excel-range"></a>Executar cálculos em um intervalo do Excel nativo

### <a name="to-run-calculations-in-a-native-excel-range"></a>Para executar cálculos em um intervalo do Excel nativo

1. Crie o intervalo nomeado.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]

2. Chamar o <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> método do intervalo especificado.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]

## <a name="see-also"></a>Consulte também
- [Trabalhar com intervalos](../vsto/working-with-ranges.md)
- [Controle NamedRange](../vsto/namedrange-control.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
