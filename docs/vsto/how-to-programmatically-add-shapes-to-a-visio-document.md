---
title: 'Como: Adicionar formas a um documento do Visio programaticamente'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09bc0ca6d0c84f87a1a1621c9028c3a147373bc5
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802651"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Como: Adicionar formas a um documento do Visio programaticamente
  Você pode adicionar formas a um documento do Microsoft Office Visio recuperando os mestres de um estêncil e descartando as formas na página ativa.  
  
 Para obter mais informações, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) método [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) propriedade, e [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) método.  
  
## <a name="add-shapes-to-a-visio-document"></a>Adicionar formas a um documento do Visio  
  
### <a name="to-add-shapes-to-a-visio-document"></a>Para adicionar formas a um documento do Visio  
  
-   Com um documento ativo, recuperar os mestres da coleção Documents.Masters e solte as formas no documento ativo. Você pode recuperar um mestre, usando o índice ou nome do mestre.  
  
     O exemplo de código a seguir cria um documento do Visio em branco e, em seguida, abre-o com o **formas básicas** estêncil encaixado. O código, em seguida, recupera várias formas e os solta na página ativa.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Trabalhar com formas do Visio](../vsto/working-with-visio-shapes.md)   
 [Como: Copiar e colar formas em um documento do Visio de forma programática](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  