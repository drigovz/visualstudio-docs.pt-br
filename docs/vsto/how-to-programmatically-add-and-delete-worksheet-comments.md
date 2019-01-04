---
title: 'Como: Programaticamente, adicionar e excluir comentários em planilhas'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: cb243498585677d6df79139bae570a9eec6270d9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968612"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Como: Programaticamente, adicionar e excluir comentários em planilhas
  Programaticamente, você pode adicionar e excluir comentários em planilhas do Microsoft Office Excel. Comentários podem ser adicionados somente para células únicas, não aos intervalos de várias células.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Adicionar e excluir comentários em um projeto de nível de documento  
 Os exemplos a seguir pressupõem que há uma única célula <xref:Microsoft.Office.Tools.Excel.NamedRange> controle chamado `dateComment` em uma planilha denominada `Sheet1`.  
  
### <a name="to-add-a-new-comment-to-a-named-range"></a>Para adicionar um novo comentário a um intervalo nomeado  
  
1.  Chame o <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> método o <xref:Microsoft.Office.Tools.Excel.NamedRange> controlar e fornecer o texto do comentário. Esse código deve ser colocado no `Sheet1` classe.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>Para excluir um comentário de um intervalo nomeado  
  
1.  Verifique se existe um comentário no intervalo e excluí-lo. Esse código deve ser colocado no `Sheet1` classe.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Adicionar e excluir comentários em um projeto de suplemento do VSTO  
 Os exemplos a seguir pressupõem que há uma única célula <xref:Microsoft.Office.Interop.Excel.Range> chamado `dateComment` na planilha ativa.  
  
### <a name="to-add-a-new-comment-to-an-excel-range"></a>Para adicionar um novo comentário a um intervalo do Excel  
  
1.  Chame o <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> método da <xref:Microsoft.Office.Interop.Excel.Range> e forneça o texto do comentário.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
### <a name="to-delete-a-comment-from-an-excel-range"></a>Para excluir um comentário de um intervalo do Excel  
  
1.  Verifique se existe um comentário no intervalo e excluí-lo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhar com planilhas](../vsto/working-with-worksheets.md)   
 [Como: Exibir comentários em planilhas de forma programática](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)  
