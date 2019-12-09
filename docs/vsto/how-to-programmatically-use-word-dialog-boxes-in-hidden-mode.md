---
title: 'Como: Usar programaticamente as caixas de diálogo do Word no modo oculto'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e32c97069e3400b447f8756f9638c9d88d38d99a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255845"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Como: Usar programaticamente as caixas de diálogo do Word no modo oculto
  Você pode executar operações complexas com uma chamada de método invocando as caixas de diálogo internas no Microsoft Office Word sem exibi-las ao usuário. Você pode fazer isso usando o <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> método <xref:Microsoft.Office.Interop.Word.Dialog> do objeto sem chamar o <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> método.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Exemplos
 Os exemplos de código a seguir demonstram como usar a caixa de diálogo **configuração de página** no modo oculto para definir várias propriedades de configuração de página sem entrada do usuário. Os exemplos usam um <xref:Microsoft.Office.Interop.Word.Dialog> objeto para configurar um tamanho de página personalizado. As configurações específicas para a configuração de página, como a margem superior, a margem inferior e assim por diante, estão disponíveis como propriedades de associação tardia <xref:Microsoft.Office.Interop.Word.Dialog> do objeto. Essas propriedades são criadas dinamicamente pelo Word em tempo de execução.

 O exemplo a seguir demonstra como executar essa tarefa em projetos Visual Basic em que **Option Strict** está off e em C# projetos visuais direcionados [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]para o. Nesses projetos, você pode usar os recursos de associação tardia nos compiladores do C# Visual Basic e do Visual. Para usar este exemplo, execute-o `ThisDocument` da classe ou `ThisAddIn` no seu projeto.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 O exemplo a seguir demonstra como executar essa tarefa em projetos Visual Basic em que **Option Strict** está on. Nesses projetos, você deve usar a reflexão para acessar as propriedades de associação tardia. Para usar este exemplo, execute-o `ThisDocument` da classe ou `ThisAddIn` no seu projeto.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Consulte também
- [Como: Usar programaticamente caixas de diálogo internas no Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)
- [Associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md)
- [Reflexão (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflexão (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
