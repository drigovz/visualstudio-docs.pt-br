---
title: 'Como: Atualizar o texto do indicador de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 12a64f35e7d530b80e44f3098035093509766c60
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113021"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Como: Atualizar o texto do indicador de forma programática
  Você pode inserir texto em um indicador de espaço reservado em um documento do Microsoft Office Word para que você possa recuperar o texto em um momento posterior, ou para substituir o texto em um indicador. Se você estiver desenvolvendo uma personalização no nível de documento, você também pode atualizar o texto em um <xref:Microsoft.Office.Tools.Word.Bookmark> controle que está associado a dados. Para obter mais informações, consulte [ligar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 O objeto de indicador pode ser um dos dois tipos:

- Um <xref:Microsoft.Office.Tools.Word.Bookmark> controle de host.

   <xref:Microsoft.Office.Tools.Word.Bookmark> controles de estendem nativo <xref:Microsoft.Office.Interop.Word.Bookmark> objetos, permitindo a ligação de dados e expor eventos. Para obter mais informações sobre controles de host, consulte [hospedam itens e visão geral dos controles](../vsto/host-items-and-host-controls-overview.md).

- Um nativo <xref:Microsoft.Office.Interop.Word.Bookmark> objeto.

   <xref:Microsoft.Office.Interop.Word.Bookmark> objetos não têm recursos de ligação de eventos ou dados.

  Quando você atribui o texto a um indicador, o comportamento difere entre uma <xref:Microsoft.Office.Interop.Word.Bookmark> e um <xref:Microsoft.Office.Tools.Word.Bookmark>. Para obter mais informações, consulte [controle de indicador](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Use os controles de host

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Para atualizar o conteúdo de indicador usando um controle de indicador

1. Criar um procedimento que usa um `bookmark` argumento para o nome do indicador e uma `newText` argumento da cadeia de caracteres atribuir ao <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> propriedade.

    > [!NOTE]
    >  Atribuição de texto para o <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> ou <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> propriedade de um <xref:Microsoft.Office.Tools.Word.Bookmark> controle não faz com que o indicador a ser excluído.

     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]

2. Atribuir o *newText* de cadeia de caracteres para o <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> propriedade o <xref:Microsoft.Office.Tools.Word.Bookmark>.

     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]

## <a name="use-word-objects"></a>Usar objetos do Word

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Para atualizar o conteúdo de indicador usando um objeto de indicador do Word

1. Criar um procedimento que tem um `bookmark` argumento para o nome da <xref:Microsoft.Office.Interop.Word.Bookmark>e um `newText` argumento da cadeia de caracteres atribuir ao <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propriedade do indexador.

    > [!NOTE]
    >  Atribuir o texto a uma palavra nativa <xref:Microsoft.Office.Interop.Word.Bookmark> objeto faz com que o indicador a ser excluído.

     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]

2. Atribuir a *newText* de cadeia de caracteres para o <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propriedade do indexador, que exclui automaticamente o indicador. Em seguida, adicione novamente o indicador para o <xref:Microsoft.Office.Interop.Word.Bookmarks> coleção.

     O exemplo de código a seguir pode ser usado em uma personalização no nível de documento.

     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]

     O exemplo de código a seguir pode ser usado em um suplemento do VSTO. Este exemplo usa o documento ativo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]

## <a name="see-also"></a>Consulte também
- [Como: Programaticamente, inserir texto em documentos do Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)
- [Controle de indicador](../vsto/bookmark-control.md)
