---
title: Intervalo inválido no caractere definido (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1cbfa4de401c2a1dc0626f8f00dbb0bd1bf24408
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007042"
---
# <a name="invalid-range-in-character-set-javascript"></a>Intervalo inválido no conjunto de caracteres (JavaScript)
Você tentou criar uma expressão regular com um intervalo de conjunto de caractere inválido. Conjuntos de caracteres devem variar desde caracteres únicos, como a-z ou 0 a 9; Você não pode incluir classes de caractere como \w em um conjunto de caracteres. O primeiro caractere no intervalo também deve vir antes do segundo caractere no intervalo. Por exemplo:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Use caracteres único apenas para compor o seu conjunto de caracteres de expressão regular e verifique se que eles estão na ordem correta.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)