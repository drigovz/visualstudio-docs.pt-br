---
title: Throw deve ser seguido por uma expressão na mesma linha de origem | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1ce004eb523497b912e8d7ec29c3b03044f0220
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861990"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>O lançamento deve ser seguido por uma expressão na mesma linha de origem
Você usou a `throw` palavra-chave, mas não a segue com uma expressão na mesma linha de origem. Uma `throw` instrução consiste em duas partes: a `throw` palavra-chave, seguida da expressão a ser gerada. Por exemplo:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Você não pode dividir esses dois componentes.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique se a `throw` palavra-chave e a expressão a serem geradas aparecem na mesma linha.  
  
## <a name="see-also"></a>Confira também  
 [Objeto de erro](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Instrução Throw](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [tentar... capturar... Instrução Finally](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)