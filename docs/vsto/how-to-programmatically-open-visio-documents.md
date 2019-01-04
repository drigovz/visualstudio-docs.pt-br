---
title: 'Como: Abrir documentos do Visio de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1815b0f336026890c88ec0794ea72911560ecb38
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875716"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Como: Abrir documentos do Visio de forma programática
  Há dois métodos para abrir documentos existentes do Microsoft Office Visio: Abra e OpenEx. O método OpenEx é idêntico ao método Open, exceto que ele forneça argumentos em que o chamador pode especificar como o documento é aberto.  
  
 Para obter detalhes sobre o modelo de objeto, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) método e [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) método.  
  
## <a name="open-a-visio-document"></a>Abra um documento do Visio  
  
### <a name="to-open-a-visio-document"></a>Para abrir um documento do Visio  
  
-   Chamar o `Microsoft.Office.Interop.Visio.Documents.Open` método e fornecer o caminho totalmente qualificado do documento do Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>Abra um documento do Visio com argumentos especificados  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Para abrir um documento do Visio como somente leitura e encaixados  
  
-   Chamar o `Microsoft.Office.Interop.Visio.Documents.OpenEx` método, forneça o caminho totalmente qualificado do documento do Visio e incluir os argumentos que você deseja usar — nesse caso, encaixado e somente leitura.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>Compilar o código  
 Este exemplo de código requer o seguinte:  
  
-   Um documento do Visio chamado `myDrawing.vsd` devem estar localizados em um diretório chamado `Test` na *Meus documentos* pasta (para o Windows XP e versões anteriores) ou o *documentos* pasta (para Windows Vista).  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Como: Criar novos documentos do Visio programaticamente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Como: Fechar documentos do Visio programaticamente](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Como: Salvar documentos do Visio programaticamente](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Como: Imprimir documentos do Visio de forma programática](../vsto/how-to-programmatically-print-visio-documents.md)  
