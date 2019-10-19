---
title: Throw deve ser seguido por uma expressão na mesma linha de origem | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 8854acb3d1992283899c4ff095f5d754c05f55a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572754"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>O lançamento deve ser seguido por uma expressão na mesma linha de origem
Você usou a palavra-chave `throw`, mas não a segue com uma expressão na mesma linha de origem. Uma instrução `throw` consiste em duas partes: a palavra-chave `throw`, seguida pela expressão a ser gerada. Por exemplo:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Você não pode dividir esses dois componentes.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Certifique-se de que a palavra-chave `throw` e a expressão a ser gerada apareçam na mesma linha.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [objeto de erro](../../javascript/reference/error-object-javascript.md)  
 [instrução throw](../../javascript/reference/throw-statement-javascript.md)    
 [Instrução try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)