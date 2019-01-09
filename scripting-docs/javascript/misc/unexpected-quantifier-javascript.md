---
title: Quantificador inesperado (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 693fdf4091a6f6fdf63c701b63c4355a67ee6fbd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096740"
---
# <a name="unexpected-quantifier-javascript"></a>Quantificador inesperado (JavaScript)
Ao redigir o padrão de pesquisa de expressão regular, você criou um elemento padrão com um fator de repetição inválida. Por exemplo, o padrão  
  
```js
/^+/  
```  
  
 é ilegal porque o elemento ^ (início da entrada) não pode ter um fator de repetição. A tabela a seguir lista os elementos que não podem ter os fatores de repetição.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|^|Início da entrada|  
|$|Fim da entrada|  
|\b|Limite de palavra|  
|\B|Limite não pertencente a palavras|  
|*|Zero ou mais repetições|  
|+|Um ou mais repetições|  
|?|Repetições de zero ou um|  
|{n}|repetições n|  
|{n}|n ou mais repetições|  
|{n, m}|De n a m repetições, inclusivas|  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se que o elemento padrão de pesquisa contém apenas fatores de repetição legal.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)