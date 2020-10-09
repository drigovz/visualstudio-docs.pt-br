---
title: Esperado '] ' na expressão regular (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 31d1ebd30ba5e793a1c52c00d8b58603bdaa9a75
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862336"
---
# <a name="expected--in-regular-expression-javascript"></a>']' esperado na expressão regular (JavaScript)
Você tentou criar uma classe de caractere para uma correspondência de expressão regular, mas não incluiu o colchete direito. Combinações de caracteres literais individuais podem ser montadas em classes de caracteres colocando-as entre colchetes. Uma classe de caractere corresponde A qualquer caractere que ela contém. Por exemplo,/[abc]/corresponde a qualquer uma das letras "a", "b" ou "c".  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Adicione o colchete direito à expressão regular.  
  
    > [!NOTE]
    > Se você quiser corresponder a um único colchete, escape-o com uma barra invertida- \\ [-portanto, ele não é interpretado como um caractere especial [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Confira também  
 [Objeto de expressão regular](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintaxe de expressão regular (JavaScript)](/previous-versions/1400241x(v=vs.100))