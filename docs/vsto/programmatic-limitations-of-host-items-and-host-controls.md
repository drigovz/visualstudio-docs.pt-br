---
title: Limitações programáticas de itens de host e controles de host
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 97b94291a3fd057e82bd79aa4f6c3220020bc24a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255810"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Limitações programáticas de itens de host e controles de host
  Cada item de host e controle de host é projetado para se comportar como uma palavra Microsoft Office nativa correspondente ou Microsoft Office objeto do Excel, com funcionalidade adicional. No entanto, há algumas diferenças fundamentais entre o comportamento de itens de host e controles de host e objetos nativos do Office em tempo de execução.

 Para obter informações gerais sobre itens de host e controles de host, consulte [visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md).

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>Criar itens de host programaticamente
 Quando você cria ou abre programaticamente um documento, pasta de trabalho ou planilha em tempo de execução usando o modelo de objeto do Word ou do Excel, o item não é um item de host. Em vez disso, o novo objeto é um objeto nativo do Office. Por exemplo, se você usar o <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> método para criar um novo documento do Word em tempo de execução, ele será um <xref:Microsoft.Office.Interop.Word.Document> objeto nativo em vez <xref:Microsoft.Office.Tools.Word.Document> de um item de host. Da mesma forma, quando você cria uma nova planilha em tempo de <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> execução usando o método, obtém <xref:Microsoft.Office.Interop.Excel.Worksheet> um objeto nativo em <xref:Microsoft.Office.Tools.Excel.Worksheet> vez de um item de host.

 Em projetos de nível de documento, você não pode criar itens de host em tempo de execução. Itens de host podem ser criados somente em tempo de design em projetos de nível de documento. Para obter mais informações, consulte [documentar](../vsto/document-host-item.md)item de host, [item de host de pasta de trabalho](../vsto/workbook-host-item.md)e item de host de [planilha](../vsto/worksheet-host-item.md).

 Em projetos de suplemento do VSTO, você pode criar <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>ou <xref:Microsoft.Office.Tools.Excel.Worksheet> itens de host em tempo de execução. Para obter mais informações, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="programmatically-create-host-controls"></a>Criar programaticamente controles de host
 Você pode adicionar controles de host programaticamente <xref:Microsoft.Office.Tools.Excel.Worksheet> a um ou a um <xref:Microsoft.Office.Tools.Word.Document> item de host em tempo de execução. Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Você não pode adicionar controles de host a <xref:Microsoft.Office.Interop.Word.Document> um <xref:Microsoft.Office.Interop.Excel.Worksheet>nativo ou.

> [!NOTE]
> Os seguintes controles de host não podem ser adicionados programaticamente a planilhas <xref:Microsoft.Office.Tools.Word.XMLNode>ou documentos <xref:Microsoft.Office.Tools.Word.XMLNodes>: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, e.

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Entenda as diferenças de tipo entre itens de host, controles de host e objetos nativos do Office
 Para cada item de host e controle de host, há um objeto de Microsoft Office nativo subjacente ou Microsoft Office do Excel. Você pode acessar o objeto subjacente usando a propriedade InnerException do item de host ou controle de host. No entanto, não há como converter um objeto do Office nativo em seu item de host ou controle de host correspondente. Se você tentar converter um objeto do Office nativo no tipo de um item de host ou controle de host, <xref:System.InvalidCastException> um será gerado.

 Há vários cenários em que as diferenças entre os tipos de itens de host e os controles de host e os objetos do Office nativo subjacentes podem afetar seu código.

### <a name="pass-host-controls-to-methods-and-properties"></a>Passar controles de host para métodos e propriedades
 No Word, você não pode passar um controle de host para um método ou propriedade que exija um objeto do Word nativo como um parâmetro. Você deve usar a propriedade InnerException do controle de host para retornar o objeto de palavra nativo subjacente. Por exemplo, você pode passar um <xref:Microsoft.Office.Interop.Word.Bookmark> objeto para um método passando a <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> Propriedade do controle de <xref:Microsoft.Office.Tools.Word.Bookmark> host para o método.

 No Excel, você deve usar a propriedade InnerException do controle de host para passar o controle de host para um método ou propriedade quando o método ou a propriedade espera o objeto subjacente do Excel.

 O exemplo a seguir cria <xref:Microsoft.Office.Tools.Excel.NamedRange> um controle e o passa para <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> o método. O código usa a <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> Propriedade do intervalo nomeado para retornar o escritório <xref:Microsoft.Office.Interop.Excel.Range> subjacente <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> que é exigido pelo método.

 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]

### <a name="return-types-of-native-office-methods-and-properties"></a>Retornar tipos de propriedades e métodos nativos do Office
 A maioria dos métodos e propriedades de itens de host retornam o objeto do Office nativo subjacente no qual o item de host é baseado. Por exemplo, a <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> propriedade de um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle de host no Excel retorna <xref:Microsoft.Office.Interop.Excel.Worksheet> um objeto em vez <xref:Microsoft.Office.Tools.Excel.Worksheet> de um item de host. Da mesma forma <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> , a propriedade <xref:Microsoft.Office.Tools.Word.RichTextContentControl> de um controle de host no <xref:Microsoft.Office.Interop.Word.Document> Word retorna um objeto <xref:Microsoft.Office.Tools.Word.Document> em vez de um item de host.

### <a name="access-collections-of-host-controls"></a>Coleções de acesso de controles de host
 O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] não fornece coleções individuais para cada tipo de controle de host. Em vez disso, use a propriedade Controls de um item de host para iterar por todos os controles gerenciados (controles de host e controles de Windows Forms) no documento ou na planilha e procure itens que correspondam ao tipo do controle de host em que você está interessado. O exemplo de código a seguir examina cada controle em um documento do Word e determina se o controle <xref:Microsoft.Office.Tools.Word.Bookmark>é um.

 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]

 Para obter mais informações sobre a propriedade Controls de itens de host, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Os modelos de objeto do Word e do Excel incluem propriedades que expõem coleções de controles nativos em documentos e planilhas. Você não pode acessar os controles gerenciados usando essas propriedades. Por exemplo, não é <xref:Microsoft.Office.Tools.Word.Bookmark> possível enumerar cada controle de host em um documento usando a <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> propriedade de <xref:Microsoft.Office.Interop.Word.Document> uma ou a <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> propriedade de um <xref:Microsoft.Office.Tools.Word.Document>. Essas propriedades incluem apenas os <xref:Microsoft.Office.Interop.Word.Bookmark> controles no documento; elas não contêm os <xref:Microsoft.Office.Tools.Word.Bookmark> controles de host no documento.

## <a name="see-also"></a>Consulte também
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Item de host de planilha](../vsto/worksheet-host-item.md)
- [Item de host da pasta de trabalho](../vsto/workbook-host-item.md)
- [Item de host do documento](../vsto/document-host-item.md)
