---
title: 'Como: verificar a ortografia em documentos programaticamente'
description: Saiba que, para verificar a ortografia em um documento programaticamente, você pode usar o método CheckSpelling.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9afbb96cce5848894c83c8780e5855eadc0e59d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836131"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Como: verificar a ortografia em documentos programaticamente
  Para verificar a ortografia em um documento, use o <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método. Esse método retorna um valor booliano que indica se o parâmetro fornecido está grafado corretamente.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Para verificar a ortografia e exibir os resultados em uma caixa de mensagem

1. Chame o <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método e passe um intervalo de texto para verificar se há erros de ortografia. Para usar este exemplo de código, execute-o `ThisDocument` da `ThisAddIn` classe ou em seu projeto.

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>Consulte também
- [Como: definir e selecionar intervalos de forma programática em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
