---
title: 'Como: programaticamente restaurar seleções após pesquisas'
description: Saiba como você pode usar o Visual Studio para restaurar as seleções programaticamente após as pesquisas em um documento do Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 493f736ce899a0d90332418ca37a5b2825dd2d7b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897508"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Como: programaticamente restaurar seleções após pesquisas
  Se você encontrar e substituir o texto em um documento, talvez queira restaurar a seleção original do usuário após a conclusão da pesquisa.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 O código no procedimento de exemplo usa dois <xref:Microsoft.Office.Interop.Word.Range> objetos. Um armazena o atual <xref:Microsoft.Office.Interop.Word.Selection> e um define o documento inteiro a ser usado como um intervalo de pesquisa.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>Para restaurar a seleção original do usuário após uma pesquisa

1. Crie os <xref:Microsoft.Office.Interop.Word.Range> objetos para o documento e a seleção atual.

    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]

2. Execute a operação de pesquisa e substituição.

    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]

3. Selecione o intervalo inicial para restaurar a seleção original do usuário.

    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]

   O exemplo a seguir mostra o método Complete.

## <a name="example"></a>Exemplo
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]

## <a name="see-also"></a>Confira também
- [Como: Pesquisar e substituir texto de forma programática em documentos](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Como: definir opções de pesquisa de forma programática no Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Como fazer loops programaticamente por meio de itens encontrados em documentos](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
