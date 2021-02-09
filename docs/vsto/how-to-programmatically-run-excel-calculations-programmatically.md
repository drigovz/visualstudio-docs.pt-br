---
title: Como executar cálculos do Excel programaticamente
description: Saiba como você pode usar o Visual Studio para executar cálculos de forma programática em uma pasta de trabalho do Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 761f58027171ccaa667aa26569e41c3b4a8b75a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880470"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Como executar cálculos do Excel programaticamente
  Você usa um processo semelhante para executar cálculos em um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ou em um objeto Range do Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Executar cálculos em um controle NamedRange
 O exemplo a seguir cria uma <xref:Microsoft.Office.Tools.Excel.NamedRange> célula at a1 e, em seguida, calcula a célula. Esse código deve ser colocado em uma classe de planilha, não na `ThisWorkbook` classe.

### <a name="to-run-calculations-in-a-namedrange-control"></a>Para executar cálculos em um controle NamedRange

1. Crie o intervalo nomeado.

     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]

2. Chame o <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> método do intervalo especificado.

     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]

## <a name="run-calculations-in-a-native-excel-range"></a>Executar cálculos em um intervalo do Excel nativo

### <a name="to-run-calculations-in-a-native-excel-range"></a>Para executar cálculos em um intervalo do Excel nativo

1. Crie o intervalo nomeado.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]

2. Chame o <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> método do intervalo especificado.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]

## <a name="see-also"></a>Confira também
- [Trabalhar com intervalos](../vsto/working-with-ranges.md)
- [Controle NamedRange](../vsto/namedrange-control.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
