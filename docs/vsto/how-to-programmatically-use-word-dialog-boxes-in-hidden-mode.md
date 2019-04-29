---
title: 'Como: Usar caixas de diálogo do Word no modo oculto de forma programática'
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
ms.openlocfilehash: e7a422e9548fabefa2066fb439c01e382586cd36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961599"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Como: Usar caixas de diálogo do Word no modo oculto de forma programática
  Você pode executar operações complexas com uma chamada de método invocando as caixas de diálogo integradas no Microsoft Office Word sem exibi-los para o usuário. Você pode fazer isso usando o <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> método da <xref:Microsoft.Office.Interop.Word.Dialog> objeto sem chamar o <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> método.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Exemplos
 Os exemplos de código a seguir demonstram como usar o **Configurar página** caixa de diálogo no modo oculto para definir as propriedades de configuração de várias página com nenhuma entrada do usuário. Os exemplos usam um <xref:Microsoft.Office.Interop.Word.Dialog> objeto para configurar um tamanho de página personalizada. As configurações específicas para a configuração de página, como a margem superior, margem inferior e assim por diante, estão disponíveis como propriedades de associação tardia do <xref:Microsoft.Office.Interop.Word.Dialog> objeto. Essas propriedades são criadas dinamicamente pelo Word em tempo de execução.

 O exemplo a seguir demonstra como realizar essa tarefa nos projetos do Visual Basic em que **Option Strict** é desativado e em projetos do Visual c# que se destinam a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Nesses projetos, você pode usar os recursos de associação tardia em que os compiladores do Visual Basic e Visual c#. Para usar este exemplo, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 O exemplo a seguir demonstra como realizar essa tarefa nos projetos do Visual Basic em que **Option Strict** está em. Nesses projetos, você deve usar a reflexão para acessar as propriedades de associação tardia. Para usar este exemplo, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Consulte também
- [Como: Usar as caixas de diálogo integradas no Word de forma programática](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)
- [Associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md)
- [Reflexão (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflexão (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
