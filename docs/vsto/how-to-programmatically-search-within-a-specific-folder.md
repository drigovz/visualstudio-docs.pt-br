---
title: 'Como: Pesquisar em uma pasta específica de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1427f0ab69cab2c23a0eeb7638bbc6e21778c55a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915488"
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
