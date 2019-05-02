---
title: 'Como: Recuperar caracteres iniciais e finais em intervalos de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 041693d5d81fb13e812b260171ec95a2bd183a6a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955661"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Como: Recuperar caracteres iniciais e finais em intervalos de forma programática
  Este exemplo demonstra como você pode recuperar as posições de caractere das posições de início e término de um intervalo.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Para recuperar caracteres iniciais e finais de um intervalo em uma personalização no nível de documento

1. Obter os valores da <xref:Microsoft.Office.Interop.Word.Range.Start%2A> e <xref:Microsoft.Office.Interop.Word.Range.End%2A> propriedades do <xref:Microsoft.Office.Interop.Word.Range> objeto. O exemplo de código a seguir obtém a posição inicial e final da segunda frase no documento. Para usar este exemplo de código, executá-la na `ThisDocument` classe em seu projeto.

     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Para recuperar caracteres iniciais e finais de um intervalo usando um suplemento do VSTO

1. Obter os valores da <xref:Microsoft.Office.Interop.Word.Range.Start%2A> e <xref:Microsoft.Office.Interop.Word.Range.End%2A> propriedades do <xref:Microsoft.Office.Interop.Word.Range> objeto. O exemplo de código a seguir obtém a posição inicial e final da segunda frase no documento ativo. Para usar este exemplo de código, executá-la na `ThisAddIn` classe em seu projeto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]

## <a name="see-also"></a>Consulte também
- [Como: Definir e selecionar intervalos em documentos programaticamente](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Como: Por meio de programação estender intervalos em documentos](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Como: Por meio de programação redefinir intervalos em documentos do Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Como: Por meio de programação recolher intervalos ou seleções em documentos](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Como: Por meio de programação excluir marcas de parágrafo ao criar intervalos](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Como: Por meio de programação contar caracteres em documentos](../vsto/how-to-programmatically-count-characters-in-documents.md)
