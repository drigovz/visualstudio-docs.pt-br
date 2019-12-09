---
title: Esperado '] ' na expressão regular (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af38a5fa754a811416f1a998b90946345f3e4a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576489"
---
# <a name="expected--in-regular-expression-javascript"></a>']' esperado na expressão regular (JavaScript)
Você tentou criar uma classe de caractere para uma correspondência de expressão regular, mas não incluiu o colchete direito. Combinações de caracteres literais individuais podem ser montadas em classes de caracteres colocando-as entre colchetes. Uma classe de caractere corresponde A qualquer caractere que ela contém. Por exemplo,/[abc]/corresponde a qualquer uma das letras "a", "b" ou "c".  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Adicione o colchete direito à expressão regular.  
  
    > [!NOTE]
    > Se você quiser corresponder a um único colchete, escape-o com uma barra invertida \\ [-portanto, ele não é interpretado como um caractere especial por [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)  
 [Sintaxe de expressão regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)