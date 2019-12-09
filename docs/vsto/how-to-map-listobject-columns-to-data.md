---
title: Como mapear colunas ListObject para dados
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cffd9f009d193f5ed687560b4f13940273fd82ad
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985893"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Como mapear colunas ListObject para dados
  Quando você associa um controle de <xref:Microsoft.Office.Tools.Excel.ListObject> a um <xref:System.Data.DataTable>, talvez você não queira exibir todas as colunas em uma lista ou pode ter determinadas colunas que não estão associadas aos dados. Você pode mapear quais colunas deseja que apareçam na <xref:Microsoft.Office.Tools.Excel.ListObject> ao chamar o método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A>.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Mapear colunas

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Para mapear uma tabela de dados para colunas em uma lista

1. Crie o <xref:System.Data.DataTable> no nível de classe.

     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]

2. Adicione colunas de exemplo e dados no manipulador de eventos `Startup` da classe `Sheet1` (em um projeto de nível de documento) ou `ThisAddIn` classe (em um projeto de suplemento do VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]

3. Chame o método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passe os nomes de coluna na ordem em que eles devem aparecer. O objeto de lista será associado ao <xref:System.Data.DataTable>recém-criado, mas a ordem das colunas no objeto de lista será diferente da ordem em que aparecem na <xref:System.Data.DataTable>.

     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]

## <a name="specify-unmapped-columns"></a>Especificar colunas não mapeadas
 Ao mapear colunas para um <xref:System.Data.DataTable>, você também pode especificar que determinadas colunas não devem ser vinculadas aos dados, passando uma cadeia de caracteres vazia. Uma nova coluna que não está associada a dados é adicionada ao controle de <xref:Microsoft.Office.Tools.Excel.ListObject>.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Para especificar uma coluna não mapeada ao mapear colunas ListObject

1. Chame o método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passe os nomes de coluna na ordem em que eles devem aparecer. Use uma cadeia de caracteres vazia para indicar onde uma coluna não mapeada é adicionada; Nesse caso, entre a coluna Title e a coluna Last Name.

     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo de código pressupõe que você tenha um <xref:Microsoft.Office.Tools.Excel.ListObject> existente chamado `list1` na planilha em que esse código aparece.

## <a name="see-also"></a>Consulte também
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Como preencher controles ListObject com dados](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Controle ListObject](../vsto/listobject-control.md)
