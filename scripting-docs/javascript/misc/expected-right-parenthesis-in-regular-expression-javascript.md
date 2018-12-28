---
title: Esperado ')' na expressão regular (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c344105010e406ef4936fdcca58baffbd610088
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802336"
---
# <a name="expected--in-regular-expression-javascript"></a>')' esperado na expressão regular (JavaScript)
Você tentou criar uma captura de expressão regular, declaração ou grupo, mas não incluiu o parêntese de fechamento. Parênteses têm várias finalidades em expressões regulares. Basicamente, eles são usados para capturar subexpressões, para especificar declarações, ou para agrupar padrões para que os itens podem ser tratados como uma única unidade pelo *, +,? e assim por diante.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicione os parênteses de fechamento mais à direita.  
  
    > [!NOTE]
    >  Se você quiser corresponder um parêntese único, isolá-lo com uma barra invertida - \\(– para que ele não será interpretado como um caractere especial por [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)