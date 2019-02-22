---
title: 'Como: Pesquisar em uma pasta específica de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 5ac3dbb169fee82a55cc41b773d3616c56f83534
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638004"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Como: Pesquisar em uma pasta específica de forma programática
  Este exemplo de código usa o `Find` e `FindNext` métodos para pesquisar texto no campo assunto de mensagens de email que estão na **caixa de entrada**. Esse método usa um filtro de cadeia de caracteres para verificar como a letra inicial da letra T o `Subject` texto.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Consulte também
- [Trabalhar com pastas](../vsto/working-with-folders.md)
- [Visão geral de modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)
- [Como: Recuperar uma pasta por nome de forma programática](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
