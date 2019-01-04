---
title: Associação tardia em soluções do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c886305b3cfe63ef2d2821752d97099d93689891
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847250"
---
# <a name="late-binding-in-office-solutions"></a>Associação tardia em soluções do Office
  Alguns tipos de modelos de objetos de aplicativos do Office fornecem funcionalidade que está disponível por meio de recursos de associação tardia. Por exemplo, alguns métodos e propriedades podem retornar diferentes tipos de objetos, dependendo do contexto do aplicativo do Office, e alguns tipos podem expor diferentes métodos ou propriedades em contextos diferentes.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Onde os projetos do Visual Basic **Option Strict** é desativado e Visual c# projetos que se destinam a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] pode trabalhar diretamente com tipos que empregam esses recursos de associação tardia.  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Valores de retorno de conversão implícita e explícita de objeto  
 Vários métodos e propriedades no Microsoft Office assemblies de interoperabilidade primários (PIAs) retornam <xref:System.Object> valores, porque elas podem retornar vários tipos diferentes de objetos. Por exemplo, o <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> propriedade retorna um <xref:System.Object> porque seu valor de retorno pode ser um <xref:Microsoft.Office.Interop.Excel.Worksheet> ou <xref:Microsoft.Office.Interop.Excel.Chart> objeto, dependendo do que é a planilha ativa.  
  
 Quando um método ou propriedade retorna um <xref:System.Object>, você deverá converter explicitamente (no Visual Basic) o objeto para o tipo correto em projetos do Visual Basic em que **Option Strict** está em. Não é necessário converter explicitamente <xref:System.Object> valores de retorno em projetos do Visual Basic em que **Option Strict** está desativado.  
  
 Na maioria dos casos, a documentação de referência lista os possíveis tipos de valor de retorno para um membro que retorna um <xref:System.Object>. Converter ou convertendo o objeto permite que o IntelliSense para o objeto no Editor de códigos.  
  
 Para obter informações sobre a conversão no Visual Basic, consulte [conversões implícitas e explícitas &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) e [função CType &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>Exemplos  
 O exemplo de código a seguir demonstra como converter um objeto para um tipo específico em um projeto do Visual Basic em que **Option Strict** está em. Esse tipo de projeto, é necessário converter explicitamente o <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propriedade para um <xref:Microsoft.Office.Interop.Excel.Range>. Este exemplo requer um projeto do Excel de nível de documento com uma classe de planilha denominada `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 O exemplo de código a seguir demonstra como converter implicitamente um objeto para um tipo específico em um projeto do Visual Basic em que **Option Strict** está desligado ou em um projeto do Visual c# que tem como alvo o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Nesses tipos de projetos, o <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propriedade é implicitamente convertida para um <xref:Microsoft.Office.Interop.Excel.Range>. Este exemplo requer um projeto do Excel de nível de documento com uma classe de planilha denominada `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="access-members-that-are-available-only-through-late-binding"></a>Acessar membros que estão disponíveis apenas por meio de associação tardia  
 Algumas propriedades e métodos nos PIAs do Office estão disponíveis apenas por meio de associação tardia. No Visual Basic, projetos where **Option Strict** está desligado ou em projetos do Visual c# que se destinam a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], você pode usar os recursos de associação tardia nestes idiomas para acessar membros de associação tardia. No Visual Basic, projetos where **Option Strict** estiver ativado, você deve usar a reflexão para acessar esses membros.  
  
### <a name="examples"></a>Exemplos  
 O exemplo de código a seguir demonstra como acessar membros de associação tardia em um projeto do Visual Basic em que **Option Strict** está desligado ou em um projeto do Visual c# que tem como alvo o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Este exemplo acessa a associação tardia **nome** propriedade da **abrir arquivo** caixa de diálogo do Word. Para usar este exemplo, executá-la na `ThisDocument` ou `ThisAddIn` classe em um projeto do Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 O exemplo de código a seguir demonstra como usar a reflexão para realizar a mesma tarefa em um projeto do Visual Basic em que **Option Strict** está em.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Consulte também  
 [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Use o tipo dynamic &#40;C&#35; guia de programação&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflexão (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflexão (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)  
