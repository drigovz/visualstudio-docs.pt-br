---
title: 'Como: pesquisar programaticamente em uma pasta específica'
description: Saiba como você pode usar o Visual Studio para pesquisar programaticamente em uma pasta específica do Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fa569a2c301cb495f109a612d817937159c257c6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524542"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Como: pesquisar programaticamente em uma pasta específica
  Este exemplo de código usa `Find` os `FindNext` métodos e para Pesquisar texto no campo assunto das mensagens de email que estão na **caixa de entrada**. Esse método usa um filtro de cadeia de caracteres para verificar a letra T como a letra inicial do `Subject` texto.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Confira também
- [Trabalhar com pastas](../vsto/working-with-folders.md)
- [Visão geral do modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)
- [Como: recuperar programaticamente uma pasta por nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
