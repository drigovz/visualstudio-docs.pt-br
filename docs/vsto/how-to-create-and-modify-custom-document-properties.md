---
title: 'Como: Criar e modificar propriedades de documento personalizadas'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d6ef8332a5adc21e25f2a414c5b359e48cf1ba7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825778"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Como: Criar e modificar propriedades de documento personalizadas
  Aplicativos do Microsoft Office listados acima fornecem propriedades internas são armazenadas com documentos. Além disso, você pode criar e modificar propriedades de documento personalizadas se há informações adicionais que você deseja armazenar no documento.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Use a propriedade CustomDocumentProperties de um documento para trabalhar com propriedades personalizadas. Por exemplo, em um projeto de nível de documento do Microsoft Office Excel, use o <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> propriedade do `ThisWorkbook` classe. Em um projeto do suplemento do VSTO para Excel, use o <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> propriedade de um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto. Essas propriedades retornam um <xref:Microsoft.Office.Core.DocumentProperties> objeto, que é uma coleção de <xref:Microsoft.Office.Core.DocumentProperty> objetos. Você pode usar o `Item` propriedade da coleção para recuperar uma propriedade específica, por nome ou índice dentro da coleção.

 O exemplo a seguir demonstra como adicionar uma propriedade personalizada em uma personalização no nível de documento para Excel e atribua um valor.

## <a name="example"></a>Exemplo
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]

## <a name="robust-programming"></a>Programação robusta
 Tentativa de acesso a `Value` propriedade para propriedades indefinidas gera uma exceção.

## <a name="see-also"></a>Consulte também
- [Suplementos do VSTO do programa](../vsto/programming-vsto-add-ins.md)
- [Personalizações em nível de documento do programa](../vsto/programming-document-level-customizations.md)
- [Como: Ler e gravar para propriedades de documento](../vsto/how-to-read-from-and-write-to-document-properties.md)
