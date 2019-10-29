---
title: 'Como: ler e gravar nas propriedades do documento'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71a4b1a84c4544f4dc2b359e391f3c9f768e8eee
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985803"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Como: ler e gravar nas propriedades do documento
  Você pode armazenar as propriedades do documento junto com um documento. Os aplicativos do Office fornecem várias propriedades internas, como autor, título e assunto. Este tópico mostra como definir propriedades de documento no Microsoft Office Excel e Microsoft Office Word.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Definir propriedades de documento no Excel
 Para trabalhar com propriedades internas no Excel, use as seguintes propriedades:

- Em um projeto de nível de documento, use a propriedade <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> da classe `ThisWorkbook`.

- Em um projeto de suplemento do VSTO, use a propriedade <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> de um objeto <xref:Microsoft.Office.Interop.Excel.Workbook>.

  Essas propriedades retornam um objeto <xref:Microsoft.Office.Core.DocumentProperties>, que é uma coleção de objetos <xref:Microsoft.Office.Core.DocumentProperty>. Você pode usar a propriedade `Item` da coleção para recuperar uma propriedade específica, seja por nome ou por índice dentro da coleção.

  O exemplo de código a seguir mostra como alterar a propriedade de **número de revisão** interna em um projeto de nível de documento.

### <a name="to-change-the-revision-number-property-in-excel"></a>Para alterar a propriedade número de revisão no Excel

1. Atribua as propriedades do documento interno a uma variável.

     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]

2. Incrementar a propriedade `Revision Number` por uma.

     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]

## <a name="set-document-properties-in-word"></a>Definir propriedades de documento no Word
 Para trabalhar com propriedades internas no Word, use as seguintes propriedades:

- Em um projeto de nível de documento, use a propriedade <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> da classe `ThisDocument`.

- Em um projeto de suplemento do VSTO, use a propriedade <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> de um objeto <xref:Microsoft.Office.Interop.Word.Document>.

  Essas propriedades retornam um objeto <xref:Microsoft.Office.Core.DocumentProperties>, que é uma coleção de objetos <xref:Microsoft.Office.Core.DocumentProperty>. Você pode usar a propriedade `Item` da coleção para recuperar uma propriedade específica, seja por nome ou por índice dentro da coleção.

  O exemplo de código a seguir mostra como alterar a propriedade de **entidade** interna em um projeto de nível de documento.

### <a name="to-change-the-subject-property"></a>Para alterar a propriedade Subject

1. Atribua as propriedades do documento interno a uma variável.

     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]

2. Altere a propriedade `Subject` para "White Paper".

     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]

## <a name="robust-programming"></a>Programação robusta
 Os exemplos pressupõem que você escreveu o código na classe `ThisWorkbook` em um projeto de nível de documento para Excel e a classe `ThisDocument` em um projeto de nível de documento para o Word.

 Embora você esteja trabalhando com o Word e o Excel e seus objetos, Microsoft Office fornece a lista de propriedades de documento internas disponíveis. A tentativa de acessar uma propriedade indefinida gera uma exceção.

## <a name="see-also"></a>Consulte também
- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)
- [Programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md)
- [Como: criar e modificar propriedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)
