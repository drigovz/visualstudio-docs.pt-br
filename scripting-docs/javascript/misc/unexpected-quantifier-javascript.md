---
title: Quantificador inesperado (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52b98875b560e4863a93849cf99c2f8756cd438a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005885"
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
|{n,}|n ou mais repetições|  
|{n,m}|De n a m repetições, inclusivas|  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique se que o elemento padrão de pesquisa contém apenas fatores de repetição legal.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)