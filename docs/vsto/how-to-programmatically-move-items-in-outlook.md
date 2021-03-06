---
title: 'Como: mover itens programaticamente no Outlook'
description: Saiba como você pode mover itens programaticamente no Microsoft Outlook. Este exemplo move as mensagens de email não lidas da caixa de entrada para uma pasta chamada test.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 770f056dc681e1ee2cd6704f9bd1d42afae4957b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888856"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Como: mover itens programaticamente no Outlook
  Este exemplo move as mensagens de email não lidas da **caixa de entrada** para uma pasta chamada **Test**. O exemplo move apenas as mensagens que têm a palavra **Test** no `Subject` campo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer:

- Uma pasta de email do Outlook chamada **Test**.

- Uma mensagem de email que chega com a palavra **Test** no `Subject` campo.

## <a name="see-also"></a>Confira também
- [Trabalhar com pastas](../vsto/working-with-folders.md)
- [Como: recuperar programaticamente uma pasta por nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Como: pesquisar programaticamente em uma pasta específica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Como executar programaticamente ações quando uma mensagem de email é recebida](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
