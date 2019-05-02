---
title: 'Como: Mover itens no Outlook de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3dcbfbe7b6e6ac5bacb9e8e36e43d780d3051903
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812546"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Como: Mover itens no Outlook de forma programática
  Este exemplo move mensagens não lidas do **caixa de entrada** para uma pasta chamada **teste**. O exemplo só move as mensagens que tenham a palavra **teste** no `Subject` campo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer:

- Uma pasta de email do Outlook chamada **teste**.

- Uma mensagem de email que chega com a palavra **teste** no `Subject` campo.

## <a name="see-also"></a>Consulte também
- [Trabalhar com pastas](../vsto/working-with-folders.md)
- [Como: Recuperar uma pasta por nome de forma programática](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Como: Pesquisar em uma pasta específica de forma programática](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Como: Executar ações programaticamente quando uma mensagem de email é recebida](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
