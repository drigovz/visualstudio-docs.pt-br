---
title: Como exibir programaticamente uma cadeia de caracteres em uma célula de planilha
description: Saiba como você pode exibir programaticamente uma cadeia de caracteres em uma célula de planilha do Microsoft Excel usando um controle NamedRange ou um objeto Range nativo do Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5a89716797ec460b461f79c94df8cea475532a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885554"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Como exibir programaticamente uma cadeia de caracteres em uma célula de planilha
  Este exemplo demonstra como exibir texto em uma célula programaticamente. Para exibir o texto na célula, use um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ou um objeto Range nativo do Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usar um controle NamedRange
 Este exemplo usa um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle chamado `message` . O controle deve ser adicionado a uma personalização no nível do documento em tempo de design. O código a seguir deve ser colocado em uma classe de planilha, não na `ThisWorkbook` classe.

### <a name="to-display-text-in-a-namedrange-control"></a>Para exibir texto em um controle NamedRange

1. Defina o valor do <xref:Microsoft.Office.Tools.Excel.NamedRange> controle como **Olá, mundo**.

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>Usar um intervalo do Excel nativo
 O código a seguir cria um novo intervalo programaticamente e atribui um valor a ele.

### <a name="to-display-text-in-an-excel-range"></a>Para exibir texto em um intervalo do Excel

1. Recupere o intervalo na célula **a1** `Sheet1` e defina o valor como **Olá, mundo**.

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>Confira também
- [Walkthrough: coletar dados usando um formulário do Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Solucionar problemas de soluções do Office](../vsto/troubleshooting-office-solutions.md)
- [Controle NamedRange](../vsto/namedrange-control.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
