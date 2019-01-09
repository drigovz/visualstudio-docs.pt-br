---
title: 'Como: Por meio de programação contar caracteres em documentos'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f6ec83d219d8f54691165b7de7008b13d3347d16
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091410"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Como: Por meio de programação contar caracteres em documentos
  É o primeiro caractere em um documento na posição do caractere 0, que representa o ponto de inserção. A última posição de caractere é igual ao número total de caracteres no documento. Você pode determinar o número de caracteres em um documento usando o <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> propriedade do <xref:Microsoft.Office.Interop.Word.Characters> coleção.  
  
 Todos os caracteres no documento são contados, incluindo espaços, marcas de parágrafo e outros caracteres que normalmente estão ocultas. Até mesmo um novo documento em branco retorna uma contagem de um caractere, porque ela contém uma marca de parágrafo.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Para exibir o número de caracteres em uma personalização no nível de documento  
  
1.  Selecione o documento inteiro.  
  
     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]  
  
2.  Exiba o número de caracteres do documento em uma caixa de mensagem.  
  
     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]  
  
## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Para exibir o número de caracteres em um suplemento do VSTO  
  
1.  Selecione o documento inteiro. O exemplo a seguir seleciona o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]  
  
2.  Exiba o número de caracteres do documento em uma caixa de mensagem.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: Recuperar caracteres iniciais e finais em intervalos de forma programática](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Como: Definir e selecionar intervalos em documentos programaticamente](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
