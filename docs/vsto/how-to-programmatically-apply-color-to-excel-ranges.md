---
title: 'Como: Aplicar cor a intervalos do Excel programaticamente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 56ecbfcdaf22132f63df1ecf5eadba97dee426af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817267"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Como: Aplicar cor a intervalos do Excel programaticamente
  Para aplicar uma cor ao texto dentro de um intervalo de células, use um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ou um objeto de intervalo do Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usar um controle NamedRange
 Este exemplo é para personalizações no nível do documento.

### <a name="to-apply-color-to-a-namedrange-control"></a>Para aplicar cor a um controle NamedRange

1. Criar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle na célula A1.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. Definir a cor do texto no <xref:Microsoft.Office.Tools.Excel.NamedRange> controle.

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Use o native intervalos do Excel

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Para aplicar cor a um objeto de intervalo do Excel nativo

1. Criar um intervalo na célula A1 e, em seguida, defina a cor do texto.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>Consulte também
- [Trabalhar com intervalos](../vsto/working-with-ranges.md)
- [Controle NamedRange](../vsto/namedrange-control.md)
- [Como: Aplicar estilos a intervalos em pastas de trabalho programaticamente](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Como: Por meio de programação se referir a intervalos de planilhas em código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
