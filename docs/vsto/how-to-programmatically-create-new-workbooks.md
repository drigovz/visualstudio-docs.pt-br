---
title: 'Como: Criar programaticamente novas pastas de trabalho'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 030bc801399ddcc73f145c0b45ca065c9a9ecc7a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251884"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Como: Criar programaticamente novas pastas de trabalho
  Quando você cria uma pasta de trabalho programaticamente, <xref:Microsoft.Office.Interop.Excel.Workbook> ela é um objeto <xref:Microsoft.Office.Tools.Excel.Workbook> nativo, não um item de host.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Você pode gerar um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host para <xref:Microsoft.Office.Interop.Excel.Workbook> um objeto no projeto de suplemento do VSTO. Para obter mais informações, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-workbook"></a>Para criar uma nova pasta de trabalho

1. Use o <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> método <xref:Microsoft.Office.Interop.Excel.Workbooks> da coleção.

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > Você pode criar uma pasta de trabalho com base em um modelo diferente do modelo padrão: passe o modelo que você deseja usar como um parâmetro <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> para o método.

## <a name="see-also"></a>Consulte também
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Trabalhar com pastas de trabalho](../vsto/working-with-workbooks.md)
- [Como: Pastas de trabalho abertas programaticamente](../vsto/how-to-programmatically-open-workbooks.md)
- [Como: Salvar pastas de trabalho programaticamente](../vsto/how-to-programmatically-save-workbooks.md)
- [Como: Fechar pastas de trabalho programaticamente](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
