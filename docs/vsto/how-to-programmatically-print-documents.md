---
title: 'Como: Imprimir documentos programaticamente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3df7ad4a5569a0c123d8c0e284ff7ad57e900355
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956038"
---
# <a name="how-to-programmatically-print-documents"></a>Como: Imprimir documentos programaticamente
  Você pode imprimir todo um documento do Microsoft Office Word ou parte de um documento, para a impressora padrão.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>Imprimir um documento que faz parte de uma personalização no nível de documento

### <a name="to-print-the-entire-document"></a>Para imprimir o documento inteiro

1. Chame o <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> método da `ThisDocument` classe em seu projeto para imprimir o documento inteiro. Para usar esse exemplo, execute o código na classe `ThisDocument`.

     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]

### <a name="to-print-the-current-page-of-the-document"></a>Para imprimir a página atual do documento

1. Chame o <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> método da `ThisDocument` de classe em seu projeto e especificar que uma cópia da página atual ser impressos. Para usar esse exemplo, execute o código na classe `ThisDocument`.

     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]

## <a name="print-a-document-by-using-a-vsto-add-in"></a>Imprimir um documento usando um suplemento do VSTO

### <a name="to-print-an-entire-document"></a>Para imprimir um documento inteiro

1. Chame o <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> método da <xref:Microsoft.Office.Interop.Word.Document> objeto que você deseja imprimir. O exemplo de código a seguir imprime o documento ativo. Para usar este exemplo, execute o código no `ThisAddIn` classe em seu projeto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]

### <a name="to-print-the-current-page-of-a-document"></a>Para imprimir a página atual de um documento

1. Chame o <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> método da <xref:Microsoft.Office.Interop.Word.Document> objeto que você deseja imprimir e especificar que uma cópia da página atual ser impressos. O exemplo de código a seguir imprime o documento ativo. Para usar este exemplo, execute o código no `ThisAddIn` classe em seu projeto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]

## <a name="see-also"></a>Consulte também
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
