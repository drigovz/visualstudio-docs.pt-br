---
title: Como criar programaticamente novas pastas de trabalho
description: Saiba como você pode criar programaticamente uma nova pasta de trabalho do Microsoft Excel usando o Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 13acd34d9883cfdc7df201dff193d261252f8a9d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963985"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Como criar programaticamente novas pastas de trabalho
  Quando você cria uma pasta de trabalho programaticamente, ela é um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto nativo, não um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Você pode gerar um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host para um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto no projeto de suplemento do VSTO. Para obter mais informações, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-workbook"></a>Para criar uma nova pasta de trabalho

1. Use o <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> método da <xref:Microsoft.Office.Interop.Excel.Workbooks> coleção.

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > Você pode criar uma pasta de trabalho com base em um modelo diferente do modelo padrão: passe o modelo que você deseja usar como um parâmetro para o <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> método.

## <a name="see-also"></a>Consulte também
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Trabalhar com pastas de trabalho](../vsto/working-with-workbooks.md)
- [Como: pastas de trabalho abertas programaticamente](../vsto/how-to-programmatically-open-workbooks.md)
- [Como: salvar pastas de trabalho programaticamente](../vsto/how-to-programmatically-save-workbooks.md)
- [Como: fechar pastas de trabalho programaticamente](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
