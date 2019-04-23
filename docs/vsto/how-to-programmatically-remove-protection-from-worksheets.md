---
title: 'Como: Remover a proteção de planilhas programaticamente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ccf7de70c3ef741119ec22f8fa9bc76868a47030
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084213"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Como: Remover a proteção de planilhas programaticamente
  Você poderá remover programaticamente a proteção de uma planilha do Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 O exemplo a seguir usa a variável `getPasswordFromUser`, que contém uma senha obtida do usuário.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Para desproteger uma planilha em uma personalização no nível de documento

1. Chamar o <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> método da planilha e passe a senha, se necessário. Este exemplo pressupõe que você está trabalhando com uma planilha denominada `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Para desproteger uma planilha em um suplemento do VSTO

1. Chamar o <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> método da planilha ativa e passe a senha, se necessário.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>Consulte também
- [Trabalhar com planilhas](../vsto/working-with-worksheets.md)
- [Como: Proteger planilhas programaticamente](../vsto/how-to-programmatically-protect-worksheets.md)
- [Como: Proteger pastas de trabalho de forma programática](../vsto/how-to-programmatically-protect-workbooks.md)
- [Como: Ocultar planilhas programaticamente](../vsto/how-to-programmatically-hide-worksheets.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
