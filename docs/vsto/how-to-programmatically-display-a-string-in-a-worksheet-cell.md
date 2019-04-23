---
title: 'Como: Exibir uma cadeia de caracteres em uma célula de planilha programaticamente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9760d019fa80d4ecae63633c38ac9df60932202
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101191"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Como: Exibir uma cadeia de caracteres em uma célula de planilha programaticamente
  Este exemplo demonstra como exibir texto em uma célula por meio de programação. Para exibir texto na célula, use um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ou um objeto de intervalo do Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usar um controle NamedRange
 Este exemplo usa uma <xref:Microsoft.Office.Tools.Excel.NamedRange> controle chamado `message`. O controle deve ser adicionado a uma personalização no nível de documento em tempo de design. O código a seguir deve ser colocado em uma classe de folha, não no `ThisWorkbook` classe.

### <a name="to-display-text-in-a-namedrange-control"></a>Para exibir texto em um controle NamedRange

1. Defina o valor da <xref:Microsoft.Office.Tools.Excel.NamedRange> o controle para **Olá, mundo**.

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>Usar um intervalo do Excel nativo
 O código a seguir cria um novo intervalo de forma programática e, em seguida, atribui um valor a ela.

### <a name="to-display-text-in-an-excel-range"></a>Para exibir texto em um intervalo do Excel

1. Recuperar o intervalo na célula **A1** nos `Sheet1` e defina o valor como **Hello World**.

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>Consulte também
- [Passo a passo: Coletar dados usando um formulário do Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Solucionar problemas de soluções do Office](../vsto/troubleshooting-office-solutions.md)
- [Controle NamedRange](../vsto/namedrange-control.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
