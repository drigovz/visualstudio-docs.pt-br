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
ms.openlocfilehash: d9a08451b186cdc3ca1526441e906cf3c9e5d4c9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866838"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Como: Pesquisar em uma pasta específica de forma programática
  Este exemplo de código usa o `Find` e `FindNext` métodos para pesquisar texto no campo assunto de mensagens de email que estão na **caixa de entrada**. Esse método usa um filtro de cadeia de caracteres para verificar como a letra inicial da letra T o `Subject` texto.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhar com pastas](../vsto/working-with-folders.md)   
 [Visão geral de modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)   
 [Como: Recuperar uma pasta por nome de forma programática](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
