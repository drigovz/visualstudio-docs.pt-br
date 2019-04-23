---
title: 'Como: Imprimir documentos do Visio de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bf492c866a43a0098fbcad5660a19c57fc90a3a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071533"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Como: Imprimir documentos do Visio de forma programática
  Você pode imprimir um documento do Microsoft Office Visio completo ou apenas uma página específica.

 Para obter detalhes sobre os métodos de impressão, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) método e [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) método .

## <a name="print-a-visio-document"></a>Imprimir um documento do Visio

### <a name="to-print-a-complete-document"></a>Para imprimir um documento completo

- Chame o `Microsoft.Office.Interop.Visio.Document.Print` método da `Microsoft.Office.Interop.Visio.Document` objeto que você deseja imprimir.

     O exemplo de código a seguir imprime o documento ativo. Para usar este exemplo, execute o código no `ThisAddIn` classe em seu projeto.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>Imprimir uma página de um documento do Visio

### <a name="to-print-a-page-of-a-document"></a>Para imprimir uma página de um documento

- Chame o `Microsoft.Office.Interop.Visio.Pages.Print` método da `Microsoft.Office.Interop.Visio.Pages` objeto que você deseja imprimir.

     O exemplo de código a seguir imprime a primeira página do documento ativo. Para usar este exemplo, execute o código no `ThisAddIn` classe em seu projeto.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Consulte também
- [Soluções do Visio](../vsto/visio-solutions.md)
- [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)
- [Como: Criar novos documentos do Visio programaticamente](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Como: Abrir documentos do Visio de forma programática](../vsto/how-to-programmatically-open-visio-documents.md)
- [Como: Fechar documentos do Visio programaticamente](../vsto/how-to-programmatically-close-visio-documents.md)
- [Como: Salvar documentos do Visio programaticamente](../vsto/how-to-programmatically-save-visio-documents.md)
