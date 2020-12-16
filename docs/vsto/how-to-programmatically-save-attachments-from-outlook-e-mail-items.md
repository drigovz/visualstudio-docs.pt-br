---
title: Salvar anexos de itens de email do Outlook programaticamente
description: Saiba como você pode usar o Visual Studio para salvar de forma programática os anexos de itens de email do Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d33c2c820f03d7fb40c953165f62943e44648082
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528248"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Como: salvar com programação anexos de itens de email do Outlook

Este exemplo salva anexos de email em uma pasta especificada quando o email é recebido na caixa de entrada.

> [!IMPORTANT]
> Este exemplo só funcionará se você adicionar uma pasta chamada **TestFileSave** na raiz do diretório C.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Confira também

- [Trabalhar com itens de email](../vsto/working-with-mail-items.md)
- [Como: recuperar programaticamente uma pasta por nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Como executar programaticamente ações quando uma mensagem de email é recebida](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Como: pesquisar programaticamente em uma pasta específica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
