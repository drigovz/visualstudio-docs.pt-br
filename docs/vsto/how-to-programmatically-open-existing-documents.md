---
title: 'Como: Abrir documentos existentes programaticamente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 490dda6e5357cd0933c6a8b494cc4373038e5c1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812373"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Como: Abrir documentos existentes programaticamente
  O <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método abre o documento do Microsoft Office Word existente, especificado por um nome de arquivo e caminho totalmente qualificado. Esse método retorna um <xref:Microsoft.Office.Interop.Word.Document> que representa o documento aberto.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Para abrir um documento

- Chame o <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método da <xref:Microsoft.Office.Interop.Word.Documents> coleta e fornecer um caminho para o documento.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>Para abrir um documento como somente leitura

- Chamar o <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método, fornecer um caminho para o documento e definir o *ReadOnly* argumento **True** na chamada do método.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo de código requer o seguinte:

- Um documento chamado *NewDocument.doc* deve existir em um diretório chamado *teste* na unidade C.

## <a name="see-also"></a>Consulte também
- [Como: Criar novos documentos programaticamente](../vsto/how-to-programmatically-create-new-documents.md)
- [Como: Fechar documentos programaticamente](../vsto/how-to-programmatically-close-documents.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
