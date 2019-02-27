---
title: Esperado ']' na expressão regular (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: 377bdd6b09c9f25b759d6bf1df2d93e9bd412be5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56839809"
---
# <a name="expected--in-regular-expression-javascript"></a>']' esperado na expressão regular (JavaScript)
Você tentou criar uma classe de caractere para uma correspondência de expressão regular, mas não incluiu o colchete direito. Combinações de caracteres literal individuais podem ser montadas em classes de caracteres, colocando-os entre colchetes. Uma classe de caracteres corresponde a qualquer caractere que ele contém. Por exemplo, / [abc] corresponde a qualquer uma das letras "a", "b", ou "c".  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicione o colchete direito à expressão regular.  
  
    > [!NOTE]
    >  Se você deseja corresponder a um único colchete, isolá-lo com uma barra invertida - \\[, então ele não será interpretado como um caractere especial por [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)