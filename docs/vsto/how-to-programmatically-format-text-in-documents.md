---
title: 'Como: Por meio de programação de formatar texto em documentos'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b9f0f64f47317b5712c34d8aca4ea6f64191438e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098981"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Como: Por meio de programação de formatar texto em documentos
  Você pode usar o <xref:Microsoft.Office.Interop.Word.Range> objeto para formatar o texto em um documento do Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 O exemplo a seguir seleciona o primeiro parágrafo no documento e altera o tamanho da fonte, o nome da fonte e o alinhamento. Em seguida, ele seleciona o intervalo e exibe uma caixa de mensagem para pausar antes de executar a próxima seção de código. A próxima seção chama o método Undo do <xref:Microsoft.Office.Tools.Word.Document> item de host (para uma personalização no nível de documento) ou o <xref:Microsoft.Office.Interop.Word.Document> classe (para um suplemento VSTO) três vezes. Ele aplica o estilo do recuo Normal e exibe uma caixa de mensagem para pausar o código. Em seguida, o código chama o <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> método uma vez e exibe uma caixa de mensagem.

## <a name="document-level-customization-example"></a>Exemplo de personalização no nível de documento

### <a name="to-format-text-using-a-document-level-customization"></a>Para formatar o texto usando uma personalização no nível de documento

1. O exemplo a seguir pode ser usado em uma personalização no nível de documento. Para usar esse código, executá-la na `ThisDocument` classe em seu projeto.

     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]

## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO

### <a name="to-format-text-using-a-vsto-add-in"></a>Para formatar o texto usando um suplemento do VSTO

1. O exemplo a seguir pode ser usado em um suplemento do VSTO. Este exemplo usa o documento ativo. Para usar esse código, executá-la na `ThisAddIn` classe em seu projeto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]

## <a name="see-also"></a>Consulte também
- [Como: Definir e selecionar intervalos em documentos programaticamente](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Como: Programaticamente, inserir texto em documentos do Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Como: Programaticamente, pesquisar e substituir texto em documentos](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
