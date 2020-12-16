---
title: 'Como: abrir documentos existentes programaticamente'
description: Saiba como usar o método Open para abrir um documento existente do Microsoft Word especificado por um caminho totalmente qualificado e um nome de arquivo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 994afc6f0d8d9bb76aff56097d0a18b8c3f940d9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525555"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Como: abrir documentos existentes programaticamente
  O <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método abre o existente Microsoft Office documento do Word especificado por um caminho totalmente qualificado e um nome de arquivo. Esse método retorna um <xref:Microsoft.Office.Interop.Word.Document> que representa o documento aberto.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Para abrir um documento

- Chame o <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método da <xref:Microsoft.Office.Interop.Word.Documents> coleção e forneça um caminho para o documento.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>Para abrir um documento como somente leitura

- Chame o <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método, forneça um caminho para o documento e defina o argumento *ReadOnly* como **true** na chamada do método.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo de código requer o seguinte:

- Um documento chamado *NewDocument.doc* deve existir em um diretório chamado *Test* na unidade C.

## <a name="see-also"></a>Veja também
- [Como criar programaticamente novos documentos](../vsto/how-to-programmatically-create-new-documents.md)
- [Como: fechar documentos programaticamente](../vsto/how-to-programmatically-close-documents.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
