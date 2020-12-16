---
title: 'Como: selecionar planilhas programaticamente'
description: Use o Visual Studio para selecionar de forma programática planilhas do Microsoft Excel com o item de host de planilha ou a coleção de planilhas da pasta de trabalho do Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5ddef833feeb4e59f5e9e9b2c95a2170ee3c2530
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528550"
---
# <a name="how-to-programmatically-select-worksheets"></a>Como: selecionar planilhas programaticamente
  O <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> método seleciona o objeto especificado, que move a seleção do usuário para o novo objeto. Use o <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> método se desejar colocar o foco no objeto sem alterar a seleção do usuário.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Se você quiser selecionar uma planilha existente em um suplemento do VSTO ou se a planilha tiver sido criada em tempo de execução em uma personalização em nível de documento, você deverá acessá-la usando a <xref:Microsoft.Office.Interop.Excel.Sheets> coleção do Excel da pasta de trabalho do Excel; caso contrário, você poderá acessar o <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host diretamente.

## <a name="use-the-worksheet-host-item"></a>Usar o item de host da planilha
 Em uma personalização no nível do documento, adicione o código a seguir a *Plan1. vb* ou *Sheet1.cs*.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Para selecionar a primeira planilha em uma pasta de trabalho usando um item de host

1. Chame o método <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> de `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usar a coleção Sheets da pasta de trabalho do Excel
 Acesse a planilha usando a coleção do Excel <xref:Microsoft.Office.Interop.Excel.Sheets> .

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Para selecionar a primeira planilha em uma pasta de trabalho usando a coleção Sheets da pasta de trabalho do Excel

1. Chame o <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> método da <xref:Microsoft.Office.Interop.Excel.Sheets> coleção para selecionar a primeira planilha da pasta de trabalho ativa.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>Veja também
- [Trabalhar com planilhas](../vsto/working-with-worksheets.md)
- [Como: imprimir planilhas programaticamente](../vsto/how-to-programmatically-print-worksheets.md)
- [Como: excluir programaticamente planilhas de pastas de trabalho](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Como: ocultar planilhas programaticamente](../vsto/how-to-programmatically-hide-worksheets.md)
- [Como: proteger planilhas programaticamente](../vsto/how-to-programmatically-protect-worksheets.md)
- [Item de host de planilha](../vsto/worksheet-host-item.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
