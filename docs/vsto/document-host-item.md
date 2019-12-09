---
title: Item de host do documento
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ebea0c3a09d08741523deddce94def170d844202
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253702"
---
# <a name="document-host-item"></a>Item de host do documento
  O <xref:Microsoft.Office.Tools.Word.Document> item de host é um tipo que estende <xref:Microsoft.Office.Interop.Word.Document> o tipo do assembly de interoperabilidade primário para o Word. O <xref:Microsoft.Office.Tools.Word.Document> item de host fornece todas as mesmas propriedades, métodos e eventos que um <xref:Microsoft.Office.Interop.Word.Document> objeto, mas também expõe eventos adicionais e atua como um contêiner para controles de host e controles de Windows Forms.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Em projetos de nível de documento, há um item <xref:Microsoft.Office.Tools.Word.Document> de host padrão que representa o documento em seu projeto. Em projetos de suplemento do VSTO, você pode gerar <xref:Microsoft.Office.Tools.Word.Document> itens de host em tempo de execução.

## <a name="understand-the-document-host-item-in-document-level-projects"></a>Entender o item de host do documento em projetos de nível de documento
 Para acessar o documento em seu projeto, use a `ThisDocument` classe. Quando você cria um projeto de nível de documento, o Visual Studio `ThisDocument` gera a classe para servir como o link de comunicação entre o Word e seu código de personalização. A `ThisDocument` classe fornece acesso a membros <xref:Microsoft.Office.Tools.Word.Document> do item de host para executar tarefas básicas em sua personalização, como a execução de código quando o documento é aberto ou fechado. Você também pode usar a classe para adicionar controles ao documento. Ao combinar diferentes conjuntos de controles e escrever código, você pode associar os controles aos dados, coletar informações do usuário e responder às ações do usuário. Para obter mais informações, consulte [programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md).

 A `ThisDocument` classe fornece um local no qual você pode começar a escrever código em seu projeto. Como a classe fornece todas as mesmas propriedades, métodos e eventos que o <xref:Microsoft.Office.Interop.Word.Document> objeto no assembly de interoperabilidade primário do Word, você também pode usar `ThisDocument` o para acessar o modelo de objeto do Word. Para obter mais informações, consulte [visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md).

### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Limitações do item de host de documento em projetos de nível de documento
 Um projeto de nível de documento pode conter apenas <xref:Microsoft.Office.Tools.Word.Document> um item de host (ou seja `ThisDocument` , a classe). Você não pode adicionar <xref:Microsoft.Office.Tools.Word.Document> novos itens de host ao seu projeto em tempo de design e não pode <xref:Microsoft.Office.Tools.Word.Document> criar novos itens de host em tempo de execução de uma personalização em nível de documento.

 Se você criar um novo documento do Word em tempo de execução, ele será do tipo <xref:Microsoft.Office.Interop.Word.Document>. Como não é um item de host, ele não pode conter controles de host nem controles de Windows Forms. Para obter mais informações sobre como criar documentos em tempo de [execução, consulte Como: Crie novos documentos](../vsto/how-to-programmatically-create-new-documents.md)programaticamente.

## <a name="understand-document-host-items-in-application-level-projects"></a>Entender os itens de host do documento em projetos de nível de aplicativo
 Em projetos de suplemento do VSTO, você pode gerar um <xref:Microsoft.Office.Tools.Word.Document> item de host em tempo de execução para qualquer documento que esteja aberto no Word. Você pode usar o <xref:Microsoft.Office.Tools.Word.Document> item de host para adicionar controles ao documento associado ou para manipular eventos que não estão disponíveis em <xref:Microsoft.Office.Interop.Word.Document> objetos.

 Para gerar um <xref:Microsoft.Office.Tools.Word.Document> item de host, use `GetVstoObject` o método. Para obter mais informações, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Consulte também
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
