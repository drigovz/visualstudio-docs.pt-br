---
title: 'Como: fechar documentos do Visio por meio de programação'
description: Saiba como você pode fechar o documento do Active Microsoft Office Visio usando o Microsoft.Office.Interop.Visio.Document. Método Close.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c1592bd500103a2db42934ab8f81392a5f1fa0d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903687"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Como: fechar documentos do Visio por meio de programação
  Você pode fechar o documento do Active Microsoft Office Visio usando o `Microsoft.Office.Interop.Visio.Document.Close` método.

 Para obter detalhes sobre esse método, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Document. Método Close](/office/vba/api/Visio.Document.Close) .

## <a name="close-the-active-document"></a>Fechar o documento ativo

### <a name="to-close-the-active-document"></a>Para fechar o documento ativo

- Chame o `Microsoft.Office.Interop.Visio.Document.Close` método para fechar o documento ativo.

     Para usar o exemplo de código a seguir, execute-o na `ThisAddIn` classe em um projeto de suplemento do VSTO para Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Confira também
- [Soluções do Visio](../vsto/visio-solutions.md)
- [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)
- [Como criar programaticamente novos documentos do Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Como: abrir documentos do Visio programaticamente](../vsto/how-to-programmatically-open-visio-documents.md)
- [Como: salvar documentos do Visio programaticamente](../vsto/how-to-programmatically-save-visio-documents.md)
- [Como: imprimir documentos do Visio programaticamente](../vsto/how-to-programmatically-print-visio-documents.md)
