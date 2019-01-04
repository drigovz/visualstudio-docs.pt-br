---
title: 'Como: Fechar documentos do Visio programaticamente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0516fcaf8f35e089752e645fbe22093ed8d87bf3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848529"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Como: Fechar documentos do Visio programaticamente
  Você pode fechar o documento ativo do Microsoft Office Visio usando a `Microsoft.Office.Interop.Visio.Document.Close` método.  
  
 Para obter detalhes sobre esse método, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) método.  
  
## <a name="close-the-active-document"></a>Fechar o documento ativo  
  
### <a name="to-close-the-active-document"></a>Para fechar o documento ativo  
  
-   Chamar o `Microsoft.Office.Interop.Visio.Document.Close` método para fechar o documento ativo.  
  
     Para usar o exemplo de código a seguir, execute-o `ThisAddIn` classe em um projeto de suplemento do VSTO para Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Como: Criar novos documentos do Visio programaticamente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Como: Abrir documentos do Visio de forma programática](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Como: Salvar documentos do Visio programaticamente](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Como: Imprimir documentos do Visio de forma programática](../vsto/how-to-programmatically-print-visio-documents.md)  
