---
title: 'Como: Remover todos os comentários de documentos programaticamente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 08d8769b20bffd5a75fb2232b1024db45b0c7b92
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870799"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Como: Remover todos os comentários de documentos programaticamente
  Use o `DeleteAllComments` método para remover todos os comentários de um documento do Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Para remover todos os comentários de um documento que faz parte de uma personalização no nível de documento  
  
1.  Chame o <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> método da `ThisDocument` classe em seu projeto. Para usar este exemplo de código, executá-la na `ThisDocument` classe.  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Para remover todos os comentários de um documento usando um suplemento do VSTO  
  
1.  Chame o <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> método da <xref:Microsoft.Office.Interop.Word.Document> da qual você deseja remover comentários.  
  
     O exemplo de código a seguir remove todos os comentários do documento ativo. Para usar este exemplo de código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: Adicionar comentários ao texto em documentos de forma programática](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Item de host do documento](../vsto/document-host-item.md)  
