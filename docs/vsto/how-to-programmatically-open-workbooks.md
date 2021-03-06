---
title: 'Como: pastas de trabalho abertas programaticamente'
description: Saiba como você pode usar o Visual Studio para abrir programaticamente uma pasta de trabalho do Microsoft Excel ou trabalhar com uma pasta de trabalho existente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5bca39b5536d5717da994808f23ee541856264ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888726"
---
# <a name="how-to-programmatically-open-workbooks"></a>Como: pastas de trabalho abertas programaticamente
  A <xref:Microsoft.Office.Interop.Excel.Workbooks> coleção no Microsoft Office Excel torna possível trabalhar com todas as pastas de trabalho abertas e abrir pastas de trabalho.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Para abrir uma pasta de trabalho existente

1. Use o <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> método da <xref:Microsoft.Office.Interop.Excel.Workbooks> coleção, passando o caminho para a pasta de trabalho.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo de código requer o seguinte:

- Uma pasta de trabalho chamada `YourWorkbook.xls` deve existir em um diretório chamado `Test` na unidade C.

## <a name="see-also"></a>Confira também
- [Trabalhar com pastas de trabalho](../vsto/working-with-workbooks.md)
- [Como: abrir arquivos de texto programaticamente como pastas de trabalho](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Como criar programaticamente novas pastas de trabalho](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Como: salvar pastas de trabalho programaticamente](../vsto/how-to-programmatically-save-workbooks.md)
- [Como: fechar pastas de trabalho programaticamente](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
